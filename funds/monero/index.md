---
layout: page
title: "MAGIC Monero Fund"
---

MAGIC Grants is pleased to offer a MAGIC Monero Fund to support the Monero ecosystem! Please make sure to familiarize yourself with the important Fund details:

* [Monero Fund Document](/funds/monero/monero_fund)
* [MAGIC Grants Policies](/about/documentation)
* [Voting Process](/funds/voting/)

## Donate

Donate to the committee and projects here: [MoneroFund.org](https://monerofund.org)

## Upcoming Dates

The next election cycle will occur in December 2024 and January 2025.

<!--
* 5 December 2023: Committee and voter nominations open
* 31 December 2023: Committee and voter nominations close
* 6 January 2024: Voting opens
* 20 January 2024: Voting closes
* ~23 January 2024: Election results announced
* 31 January 2024: Newly elected members join the committee
-->

## Committee Candidates and Voter Nominations

[Announce your candidacy, view the candidacy of others, and apply to be a voter on GitHub](https://github.com/MAGICGrants/Monero-Fund-Elections). You need a GitHub account to be a committee member candidate.

## Existing Committee Members and Voters

Committee Members:
* monerobull (term until 2025-01)
* artlimber (term until 2025-01)
* kowalabearhugs (term until 2025-01)
* Rucknium (term until 2026-01)
* kayabaNerve (term until 2026-01)

[List of all voters](/funds/monero/monero_fund_voters)

## MAGIC Monero Fund Achievements

* Built open source crowdfunding platform [MoneroFund.org](https://monerofund.org)
* Funded [Security Audit of Ring Signature Resiliency Against Machine/Deep Learning Attacks](https://github.com/MAGICGrants/Monero-Fund/issues/15) by ACK-J for $12,000
* Funded [4 months of ETH-XMR atomic swap research and development](https://www.gofundme.com/f/noot-ethxmr-atomic-swap-development-4-months) by noot for $23,477

## MAGIC Monero Fund Vision and Goals

* Improve the Monero ecosystem.
* Support Monero development and research.
* Create Monero educational resources.
* Fund Monero security audits.
* Run essential services that support the Monero ecosystem.

## Other ways to contribute

Donate cryptocurrency and fiat on [MoneroFund.org](https://monerofund.org).

## Committee Minutes

<ul class="post-list">
{% assign monerofundminutes = site.monerofundminutes | sort: 'date' | reverse %}
{% for minute in monerofundminutes limit:5 %}
  <li><article><a href="{{ site.url }}{{ minute.url }}"><div class="post-entry-title">{{ minute.title }}</div> <span class="entry-date"><time datetime="{{ minute.date | date_to_xmlschema }}">{{ minute.date | date: "%B %d, %Y" }}</time></span>{% if minute.excerpt %} <span class="excerpt">{{ minute.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</span>{% endif %}</a></article></li>
  <hr>
{% endfor %}
</ul>

[Archive of older minutes](https://github.com/MAGICGrants/website/tree/master/posts/_monerofundminutes)
