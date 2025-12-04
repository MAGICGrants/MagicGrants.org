---
layout: page
title: "MAGIC Monero Fund"
---

MAGIC Grants is pleased to offer a MAGIC Monero Fund to support the Monero ecosystem! Please make sure to familiarize yourself with the important Fund details:

* [Monero Fund Document](/funds/monero/monero_fund)
* [MAGIC Grants Policies](/about/documentation)
* [Voting Process](/funds/voting)

## Donate

Donate to the committee and projects here: [donate.magicgrants.org/monero](https://donate.magicgrants.org/monero)

## Merchandise

The MAGIC Monero Fund has a shop where you can support them by purchasing merchandise.

[Monero Fund Shop](https://shop.monerofund.org){: .btn-secondary}

## Upcoming Dates


<!-- The next election cycle will occur in December 2025 and January 2026. -->


* 5 December 2025: Committee and voter nominations open
* 31 December 2025: Committee and voter nominations close
* 6 January 2026: Voting opens
* 20 January 2026: Voting closes
* ~23 January 2026: Election results announced
* 31 January 2026: Newly elected members join the committee


## Committee Candidates and Voter Nominations

[Announce your candidacy, view the candidacy of others, and apply to be a voter on GitHub](https://github.com/MAGICGrants/Monero-Fund-Elections). You need a GitHub account to be a committee member candidate.

## Existing Committee Members and Voters

Committee Members:
* ack-j (term until 2027-01)
* kowalabearhugs (term until 2027-01)
* rottenwheel (term until 2026-01)

[List of all voters](/funds/monero/monero_fund_voters)

## MAGIC Monero Fund Achievements

* Improved [Monero fuzzing](https://magicgrants.org/2025/11/17/Monero-RPC-Fuzzing)
* Built open source crowdfunding platform [MoneroFund.org](https://monerofund.org) (which was later expanded into [donate.magicgrants.org](https://donate.magicgrants.org))
* Funded [Security Audit of Ring Signature Resiliency Against Machine/Deep Learning Attacks](https://github.com/MAGICGrants/Monero-Fund/issues/15) by ACK-J for $12,000
* Funded [4 months of ETH-XMR atomic swap research and development](https://www.gofundme.com/f/noot-ethxmr-atomic-swap-development-4-months) by noot for $23,477

## MAGIC Monero Fund Vision and Goals

* Improve the Monero ecosystem.
* Support Monero development and research.
* Create Monero educational resources.
* Fund Monero security audits.
* Run essential services that support the Monero ecosystem.

## Other ways to contribute

Donate cryptocurrency and fiat at [donate.magicgrants.org/monero](https://donate.magicgrants.org/monero).

## Committee Minutes

<ul class="post-list">
{% assign monerofundminutes = site.monerofundminutes | sort: 'date' | reverse %}
{% for minute in monerofundminutes limit:5 %}
  <li><article><a href="{{ site.url }}{{ minute.url }}"><div class="post-entry-title">{{ minute.title }}</div></a></article></li>
  <hr>
{% endfor %}
</ul>

[Archive of older minutes](https://github.com/MAGICGrants/MagicGrants.org/tree/master/posts/_monerofundminutes)
