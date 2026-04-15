---
layout: post
title: "Serai Substrate Blockchain Components Audited by SRLabs"
excerpt: "MAGIC Grants commissioned SRLabs to audit Serai's Substrate blockchain components"
date: 2026-04-15
author: magicboard
---

MAGIC Grants contracted [SRLabs](https://srlabs.de), a leading telecom and Polkadot research firm, to audit the core Substrate blockchain components that are expected to be used by Serai. [Serai](https://serai.exchange) is a forthcoming decentralized exchange that will initially be compatible with the Ethereum, Bitcoin, and Monero blockchains.

Serai is open-source and has a strong potential to be important public infrastructure. Thus, security reviews are essential to ensure the safety of its components.

Serai has been designed to be agnostic to what underlying blockchain technology it uses, and it allows for the ability to migrate to another system later if deemed appropriate. Using Polkadot's Substrate was preferable to designing these blockchain components from scratch.

The SRLabs audit was prepared by Jonas Panizza, Nils Ollrogge, Gabriel Arnautu, and Marc Heuse.

SRLabs's review occured over eleven weeks. They focused on assessing Serai's codebase for resilience against hacking and abuse scenarios. Key areas of scrutiny included all Substrate pallets, the Serai node and runtime, the build pipeline, and the custom patches to Polkadot SDK that the Serai team created. The testing approach combined static and dynamic analysis techniques, leveraging both automated tools and manual inspection. They prioritized reviewing critical functionalities and conducting thorough security tests to ensure the robustness of Serai’s codebase and the theory behind it.

SRLabs identified several issues ranging from high to informational level severity. Most of the identified issues were DoS vectors enabling attackers to trigger panics in the blockchain runtime. Luke Parker, the lead Serai developer, acknowledged these issues and has remediated most of them. A few outstanding issues remain and will be fixed before the Serai network goes live. Serai accepted the risk (without making changes) for [one information level severity issue](https://github.com/serai-dex/serai/issues/774).

MAGIC Grants would like to thank SRLabs for their detailed review of this project, and we would like to thank Luke Parker for their efforts in developing Serai. SRLabs was especially accommodating with this staged review process.

[Read the Audit Report](/files/2026-04-01-SRL-Serai_baseline_assurance_report.pdf){: .btn-primary}

[Read Serai's Commentary](https://serai.exchange/2026/04/15/serai-blockchain-audited.html){: .btn-secondary}
