---
layout: post
title: "Comparing MAGIC Funds and Gitcoin"
excerpt: "Gitcoin is often discussed in charitable cryptocurrency conversations, but it is not a charity."
date: 2021-12-23
author: magicboard
---

A lot of cryptocurrency charitable conversations involve [Gitcoin](https://gitcoin.co) in some capacity. Gitcoin has raised millions of dollars, especially for projects in the Ethereum ecosystem.

While we believe Gitcoin has unquestionably done some good for the cryptocurrency space, we believe that donors, communities, and grantors need to understand what Gitcoin is and isn't.

If you're on this page, you've probably heard of Gitcoin but aren't extremely familiar with it.

## What is Gitcoin?

[Gitcoin](https://gitcoin.co) is a *for-profit* platform that allows people to donate funds (primarily using Ethereum) to various developers and organizations they would like to support.

Gitcoin's consists of several parts that are sometimes confused (and others we think are less relevant for this post):

* Campaigns where projects ask for donations (called "Grants").
* Bounties where people can put up money to be paid when tasks are complete (a 10% fee (unless waived) applies).
* Special matching funds for Grants from various donors.

Grants can be opened by many different organizations or developers. You'll see advocacy groups (like the 501(c)(4) [Coin Center](https://gitcoin.co/grants/1668/coin-center-is-educating-policy-makers-about-publ)), public charities (like the 501(c)(3) [Electronic Frontier Foundation](https://gitcoin.co/grants/3974/electronic-frontier-foundation)), and open source projects (like [Rotki](https://gitcoin.co/grants/149/rotki-the-portfolio-tracker-and-accounting-tool-t)).

Developers are primarily interested in seeing what bounties exist so that they can work on those. Gitcoin facilitates the formation of contracts between these developers ("Hunters") and bounty posters ("Posters"), but Gitcoin is not a party in this service contract.

The matching funds differentiate Gitcoin from just another fundraising platform. Gitcoin works with several large donors (and small ones, especially in the case of [some pools](https://gitcoin.co/grants/12/gitcoin-grants-official-matching-pool-fund)) to create pools of funds to be used for specific matching purposes. 

## How Gitcoin pools and matching work

Gitcoin consolidates funds in various pools. These pools are unique to a given active matching round.

These pools vary each round, but [GR12](https://gitcoin.co/blog/announcing-grants-round-12/) (ended 2021-12-16) included 1) a generic pool, and 2) and many specific pools to address climate change, advocacy, longevity, and specific ecosystems like Uniswap.

For simplicity's let's just focus on one big pool, but there are many in practice. Focusing on one makes matching easier to understand.

Charities have used matching often in the past in a relatively basic way to encourage more donations. For example: for each $1 you donate, another entity will match that $1 to double the donation. It can take various forms, but that's the basic idea.

Gitcoin matches funds in a *completely* different way using "Quadratic Funding." Instead of proportionally matching on dollars alone, Gitcoin matches in large part by the *total number of donation.* This means that a Grant with 10 donations of $10 (A) get a *significantly* higher portion of the pooled matching funds (suppose $100) than a Grant with 1 donation of $100 (B).

| Matching Type | Received by A | Received by B |
| --- | --- | --- |
| Normal | $100 + $50= $150 | $100 + $50 = $150 |
| Quadratic | $100 + $90.91 = $191.91 | $100 + $9.09 = $109.09 |

Despite both projects raising $100 each, Project A raises nearly double what Project B raises after matching.

Proponents of Gitcoin and Quadratic Funding argue that small donations are more important than their direct values show. Critics argue that this encourages the spamming of small donations, or that significant drawbacks need to be imposed to mitigate these risks.

Gitcoin uses a combination of methods to mitigate these risks, including Twitter/Facebook/video verification and an investigation process.

MAGIC Grants has no specific position on using Quadratic Voting to allocate matching funds. We could potentially use this or a similar method should we ever receive a donation that was supposed to be distributed amongst several funds. Still, the downsides involved with needing to verify accounts for your donation to count as much are significant, and they would put off a lot of MAGIC Grants's existing donor community. Traditional matching has downsides, but at least it's straightforward.

## Be careful of the matching estimates

Gitcoin shows matching estimates. At one point, the platform claimed that a [$1 contribution would be matched by $3204](https://twitter.com/NeerajKA/status/1466812177260679177). Coin Center raised a significant amount of money in the round: $103,839. However, [they received $340,000 in matching](https://youtu.be/W-doVjkkZbg?t=2643), or "only" a $3.27 match for every $1 on average.

While this is still generous matching, it's important to be cautious that these estimates are not definitive in any sense. Instead of participating in a straightforward matching process, you are participating in a far more complicated one.

## Tax deductions? It's complicated.

Donations on Gitcoin can get complicated, but they largely *are not tax deductible.* The IRS requires people to donate to qualifying nonprofits to deduct their donation.

If you use Gitcoin to donate to a 501(c)(3) like the EFF, then your donation to them *should* be tax deductible. If you donate funds to a Gitcoin matching pool or to an entity that's not a 501(c)(3), it's likely not tax deductible. If you donate a portion to the EFF and another portion to a pool, only the first part would be deductibe.

Things may get especially complicated if you donate to a pool, which then donates a certain percentage to 501(c)(3) organizations. You need to ask a tax expert if any fraction of that donation to the pool is deductible, or if it's a lost opportunity cost.

Tax deductions are extremely valuable to many individuals and entities. If we compare the implications of creating a qualifying bounty with MAGIC Funds compared to Gitcoin, it could be as much as 40% cheaper in practice with MAGIC Grants.

## Gitcoin is not a charity

Gitcoin is a Delaware corporation with no special charitable exemptions from the IRS ([search for](https://apps.irs.gov/app/eos/allSearch) "Gitcoin Holdings Inc."). It is a for-profit company that has raised [$11.3 million](https://gitcoin.co/blog/gitcoin-grows-treasury-to-accelerate-open-source/) from Paradigm, IDEO, 1kx, Electric Capital, Naval, Balaji, The LAO, MetaCartel Ventures, and others.

MAGIC Grants is a Colorado nonprofit corporation with 501(c)(3) public charity exemption [from the IRS](https://apps.irs.gov/app/eos/detailsPage?ein=825183590&name=Multidisciplinary%20Academic%20Grants%20in%20Cryptocurrencies&city=Boulder&state=CO&countryAbbr=US&dba=&type=CHARITIES,%20DETERMINATIONLETTERS,%20COPYOFRETURNS&orgTags=CHARITIES&orgTags=DETERMINATIONLETTERS&orgTags=COPYOFRETURNS). MAGIC Grants has no investors, just a charitable board.

Since Gitcoin is not a 501(c)(3) exempt charity, donations to Gitcoin are not tax deductible. Donations to MAGIC Grants and MAGIC Funds are fully tax deductible.

## Comparing the benefits and drawbacks of Gitcoin and MAGIC Funds

### Benefits of Gitcoin

* Quirky matching method that gathers a lot of attention and encourages community engagement.
* Good connections through its investors.
* Has (to some extent) facilitated millions of dollars in grants.
* Easy way of allocating money to community-supported projects: just send it to the matching pool you want.
* Easy platform for posting Grants and Bounties.

### Drawbacks of Gitcoin

* Donation transactions are often costly on blockchains, and Gitcoin requires blockchain payments.
* Possible opportunity cost of tax deductions if you donate to a matching pool and the pool gives a portion to a qualifying entity.
* Run by a for-profit entity. Many donations are not tax deductible.
* Encourages verification through bad privacy measures, like linking Facebook, Twitter, SMS phone number, etc.

### Benefits of MAGIC Funds

* Donations are completely tax deductible, with up to 37% savings on federal taxes *alone*. That would let you donate $100 for only $63, even before any matching.
* Donations are accepted by cryptocurrency, wire, check, NFT, etc.
* Assets can (optionally) be invested through innovative means, for example by providing liquidity on a DEX or lending on a cryptocurrency lending platform.
* MAGIC Funds include project communities in decisions by selecting voters to elect advisory committees.
* The organization is able to directly sign contracts with and face grant recipients.
* MAGIC Funds allow community-elected leadership positions wide autonomy to grow the Fund.
* MAGIC Grants can set up matching programs for various Funds or fundraising campaigns in a much more straightforward manner.
* MAGIC Grants publishes various public financial documents that are required by law.
* MAGIC Grants is explicitly not-for-profit by law. MAGIC Grants's board cannot receive compensation for being a board member.

### Drawbacks of MAGIC Funds

* MAGIC Funds can only fund specific types of projects. MAGIC Funds can only support projects that qualify as public infrastructure, and the activities are mostly limited to educational resources, scholarships, research, development, and security audits. MAGIC Funds could not, for example, fund advocacy/lobbying groups like Coin Center.
* MAGIC Grants does not have a grant platform at the moment.
* Though MAGIC Grants has handled >$100,000, we haven't handled millions in assets yet.

## The direct impact of tax deductions

Let's say that a large donor and a small donor want to give back to the Bitcoin community by supporting research and development.

The large donor pledges to match, dollar for dollar, up to $1 million in donations. The small donor wishes to give $1000.

On Gitcoin, this would likely cost both donors the full value of their donations. The donation to the pool would most likely not be deductible at all, or only partially deductible in the best case. The small donor can only claim a deduction if they donate directly to a 501(c)(3) that supports Bitcoin research and development.

Most likely, the real cost to donate $1000 from each of these two donors is $2000 total. No savings.

If instead these donors gave money to a MAGIC Bitcoin Fund, then they should both qualify for tax deductions. The real savings for businesses and individuals is about 20%, but it could be greater. So the cost of donating $1000 each is only ~$1600 total.

This MAGIC Bitcoin Fund would then select researchers and developers to fund with the donations.

Where possible, people and organizations should donate in ways to maximize their tax deductions. Especially when talking about large sums of money like the $1 million matching pledge, that results in hundreds of thousands of additional dollars going towards these ecosystems.

## Conclusion

Hopefully you now have a better idea of the similarities and differences between Gitcoin and MAGIC Funds. Gitcoin is a for-profit company that operates a grant crowdfunding site and uses a quirky pool matching program. MAGIC Funds are a part of a 501(c)(3) public charity.

We encourage donors to [reach out to us](mailto:info@magicgrants.org) to see if we can help take your donation further with tax advantages while still supporting the projects you are passionate about.

*Note: this is not legal or tax advice; talk to a legal/tax professional.*
