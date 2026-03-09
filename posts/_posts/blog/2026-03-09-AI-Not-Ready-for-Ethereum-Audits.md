---
layout: post
title: "AI Is Not Ready for Security Audits"
excerpt: "A specialized smart contract auditing AI tool made up a bug and suggested introducing the same critical vulnerability to fix it"
date: 2026-03-09
author: magicboard
---

> A specialized smart contract auditing AI tool made up a bug and suggested introducing the same critical vulnerability to fix it.

Last year, MAGIC Grants raised funds for and [contracted](/posts/_posts/blog/2025-06-06-Serai-Ethereum-Smart-Contract.md) a human-led review of an Ethereum smart contract.

Like most audits, it paid dividends. While the auditors found that the code in scope followed best practices for development and was well documented, [the review](https://github.com/trailofbits/publications/blob/master/reviews/2025-04-serai-dex-security-review.pdf) produced two information-severity findings and three code quality suggestions. Zero high, medium, and low-severity findings were discovered.

High-quality security audits are essential to mitigate the risks of catastrophic security or privacy loss. Although reviews are very expensive, paying top talent to review very sensitive code is worth the cost.

We observed [Zellic](https://www.zellic.io/), a high-quality research firm in our experience, post about their AI-based auditing tool [V12](https://v12.zellic.io/), which they describe as "The only autonomous Solidity auditor that finds critical bugs."

Zellic is clear on the V12 website that the AI tool is "not an official Zellic audit."

Zellic co-founder Luna Tong [recently shared](https://x.com/gf_256/status/2028682761234485753) that V12 scored 70.6% on EVMBench detect. [EVMBench](https://openai.com/index/introducing-evmbench/) is a benchmark created by OpenAI and Paradigm that "evaluat[es] the ability of AI agents to detect, patch, and exploit high-severity smart contract vulnerabilities."

MAGIC Grants added the Serai Ethereum smart contract to V12 to see how it would perform. A good AI tool would accurately report potential vulnerabilities while avoiding false positives.

While the cost of the AI review was effectively nothing ($5.66 of a $50 free credit), sadly the value of the review was also zero.

V12 reported four vulnerabilities, two of which it marked as "invalid" automatically (one critical and one low). That left two: one critical severity and one "low-confidence" low severity.

This is not a hit piece on the creators of this tool. We support high quality, battle-tested software, and we support efforts to increase security. Other security research firms are also experimenting with AI. However, it's clear that this tool will not undermine their primary line of business; human reviews and expertise are still necessary.

We reached out to Zellic, and they did not provide a comment.

Let's get into the report.

## The Critical-Severity False Positive

V12 claimed a critical vulnerability entitled "ETH transfers fail for contracts."

A copy of its report is shown below:

```
The native-coin branch sends ETH using `call` with a gas argument of `0`, which forwards only the 2,300‑gas stipend when value is transferred. Any contract recipient with a non‑trivial `receive` or `fallback` will run out of gas and make the call fail. Because `transferOut` is the internal primitive used by both `execute4DE42904` and the escape hatch, those higher‑level paths cannot deliver ETH to contract recipients, including a designated escape contract. If callers revert on failure the whole batch becomes unexecutable; if they ignore it, ETH remains trapped in the router. This creates a denial‑of‑service condition for ETH withdrawals to contracts.

Root cause

ETH transfers are performed with a 2,300‑gas stipend (`call` with gas=0), which is insufficient for many contract recipients.

Affected locations

    Router.transferOut

    Single finding location

Impact

Legitimate ETH withdrawals to contract wallets or vaults can fail, preventing users or the escape mechanism from receiving ETH. In the worst case, ETH held by the router becomes effectively locked because transfers to the required contract destination never succeed.
```

The suggested remediation was to:

```
Forward available gas in the native-coin `transferOut` path by using `gas()` instead of `0`, preventing ETH transfers to contracts from failing due to the 2,300 stipend.
```

So, is this critical report accurate? Did V12 discover something that a team of highly qualified humans missed?

No.

V12 fundamentally misunderstood the problem. A decentralized exchange smart contract needs to send ETH, but the protocol also needs to remove the risk of having its assets drained by paying absurdly high gas (transaction) fees. An illicit actor could attempt to force the smart contract to pay way more gas than appropriate, resulting in the protocol (or rather, the relayer acting in service of the protocol) losing ETH in the process.

The existing code handles this by refusing to send ETH if the gas exceeds the 2,300 gas stipend. This is [a well-known limit](https://docs.soliditylang.org/en/develop/contracts.html#receive-ether-function), with years of discussion on associated best practices and how to write compatible contracts. It's true this doesn't enable receiving directly to contracts with fallback methods which do more than emit a single event, but this fact about the EVM fundamentally discourages fallback/receive functions which use more than 2,300 units of gas. Serai, at worst, makes a design decision perpetuating this rough edge of the EVM in order to ensure it can bound its gas consumption.

V12 suggested to allow the contract to spend infinite gas (essentially, a blank check). Arguably, the suggested fix for this reported bug is to introduce a high or critical severity bug. This would allow any recipient to force the entire transaction to run out of gas and revert, stalling all transfers from the Serai network unless the problematic transfers are dropped.

V12 also missed certain subtleties of the code, such as claiming that attackers could input an address they know will cause a payment failure to cause a denial of service that prevents all transfers from the network from succeeding. This isn't correct either, as the current contract will note such transfers as failed and continue on due to bounding the amount of gas transfers may use. It's actually the suggested remediation which allows reverting the entire transaction and introduces this alleged critical issue.

The critical finding did include two notes which could be considered as valid informational issues, how the contract does propagate the worst-case of this rough edge by only propagating 2,300 gas (not a higher limit, or a user-specified limit), and how this rough edge is further exposed to any escape hatch. For the former note, another method does allow the user to specify the gas limit, and for the latter, the escape hatch may be "invalid" in a variety of ways and is trusted to work.

This reported critical bug was not tagged as low-confidence.

## The Low-Severity False Positive

To V12's credit, it reported this low-security vulnerability as low-confidence. V12 states "Low-confidence findings are more likely to be false positives. Review before treating as confirmed issues. Low-confidence findings are more likely to be false positives. Review before treating as confirmed issues."

The title of this reported vulnerability is "Deposit amount not reconciled with received tokens."

A copy of its report is shown below:

```
For ERC20 deposits the function performs a low-level `transferFrom` and then immediately emits `InInstruction` using the caller-supplied `amount`. It never checks the router’s token balance before and after the call, so tokens with transfer fees, burns, or non‑standard behavior can transfer fewer tokens than requested while still returning success. The emitted event therefore becomes an overstated record of the deposit. Because the router is designed to drive off‑chain signed instructions from these deposits, the recorded amount can be larger than the actual assets held. An attacker can exploit this mismatch by depositing a deflationary or malicious token and getting credit for more than was transferred.

Root cause

The function trusts the `amount` parameter and the `transferFrom` return value without verifying the actual balance change in the router.
Affected locations

    Router.inInstruction

    Single finding location

Impact

An attacker can underpay on deposit yet produce an event that reflects a larger deposit, leading the system to credit more than was actually received. If outbound instructions rely on this event, the attacker can withdraw the overstated amount, draining pooled liquidity or causing later transfers to revert due to insufficient balance.
```

This finding might be useful in isolation. If the Serai protocol intended to support non-standard ERC20 tokens, then it would be useful for a developer to know this limitation.

However, [Serai's code includes a comment](https://github.com/serai-dex/serai/blob/e962cf49c8bb61f5779f10ad342cd075457bfd1b/processor/ethereum/router/contracts/Router.sol#L329-L350) within the file that V12 reviewed that states the following:

```
Due to fee-on-transfer tokens, emitting the amount directly is frowned upon. The amount instructed to be transferred may not actually be the amount transferred.

If we add nonReentrant to every single function which can effect the balance, we can check the amount exactly matches. This prevents transfers of less value than expected occurring, at least, not without an additional transfer to top up the difference (which isn't routed through this contract and accordingly isn't trying to artificially create events from this contract).

If we don't add nonReentrant, a transfer can be started, and then a new transfer for the difference can follow it up (again and again until a rounding error is reached). This contract would believe all transfers were done in full, despite each only being done in part (except for the last one).

Given fee-on-transfer tokens aren't intended to be supported, the only token actively planned to be supported is Dai and it doesn't have any fee-on-transfer logic, and how fee-on-transfer tokens aren't even able to be supported at this time by the larger Serai network, we simply classify this entire class of tokens as non-standard implementations which induce undefined behavior.

It is the Serai network's role not to add support for any non-standard implementations.
```

A human reviewer would have noted this context and probably not have raised the issue at all, since the documentation that covers this exact point already exists.

## Other Reported Auto-Invalidated Findings

We don't want to focus on the two findings that V12 auto-invalidated as likely incorrect, but the contents of those findings were also suspect.

One included finding suggested using "address(this).nonce" instead of the in-contract nonce tracking it believed erroneous. While the in-contract nonce tracking functioned as expected, which is presumably why the AI invalidated its own 'finding,' the suggested mediation is to use something that doesn't exist, explaining why Serai handled this internally.

The other automatically invalidated finding misunderstood the approval flow and initially wrote (before auto-invalidating) about a classic bug regarding repeat approvals to the same address, not grasping how each approval is intended to be legitimate on its own and are only made to unique addresses.

## Summary

Is AI doomed to be useless? No, not necessarily. It can help developers find certain classes of bugs at way lower cost than using experienced human reviewers.

It's clear that AI assisted tools can make serious mistakes. Not only can they report false positives, but they can suggest fixes that introduce major vulnerabilities.

While only costing $5.66 in (free) credits, there was also the human cost of reviewing this report for its integrity which it largely lacked and didn't justify.

Sensitive code needs to be treated with caution. Developers need to understand what the code they intend to use does. While AI review can play a part in that, its current limitations mean it should play a minor (or no) part, and in no cases should AI _replace_ experienced auditors.

If an AI tool created by experienced, competent reviewers for the explicit purpose of reviewing programs like the one we fed it here made this significant of a mistake, this is a clear demonstration that all security-oriented AI tools need to be heavily scrutinized.

If your project needs help finding talented reviewers, email us at [info@magicgrants.org](mailto:info@magicgrants.org). MAGIC Grants is a 501(c)(3) public charity that supports public cryptocurrency infrastructure.
