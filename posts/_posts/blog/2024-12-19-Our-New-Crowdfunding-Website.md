---
layout: post
title: "Our New Campaign Website"
excerpt: "MAGIC Grants has released our new crowdfunding website for our funds and campaigns."
date: 2024-12-19
author: magicboard
---

MAGIC Grants is happy to announce [our new crowdfunding website donate.magicgrants.org](https://donate.magicgrants.org), which will serve as the main location to keep track of our fundraising campaigns.

This new campaign website will allow our organization and communities supported by our [MAGIC Funds](/funds) to more easily raise funds for our charitable mission.

The campaign website supports donations with cryptocurrencies and with credit/debit card.

## Embracing Open Source

The entire crowdfunding website is open-source, and it is built upon other FOSS software including the following:

* [BTCPay Server](https://btcpayserver.org/)
* [OpenSats](https://github.com/OpenSats/website/)
* [Keycloak](https://www.keycloak.org/)
* [Strapi](https://strapi.io/)
* [Bitcoin](https://en.wikipedia.org/wiki/Bitcoin) and [Monero](https://getmonero.org)

Our main repository for the website is available on [this GitHub repository](https://github.com/MAGICGrants/campaign-site/).

## Enhancing Security

We did not want to rely upon a third-party custodian to receive cryptocurrency donations. We want to receive donations directly into our own self-custody wallets.

We rely upon our self-hosted instance of BTCPay Server to track incoming donations in Bitcoin and Monero, but we do not store the private keys to our wallets on the campaign website or the BTCPay Server instance. Instead, view-only keys track incoming funds without these keys being able to spend. This helps to keep the funds that we receive safe.

## Supporting Donors

We have more options and features for donors than ever before! 

Donors can choose to easily receive their automated donation receipt by email. [Donations](/contribute) to MAGIC Grants, a 501(c)(3) public charity, may qualify for a tax deduction.

Donors can optionally create an account to more easily keep track of the projects that they have supported.

Donors can optionally receive points back for their donation, which they can then redeem on various perks. Our vision for perks include merchandise and gift cards to services that share aspects of our charitable mission. If you choose to receive perks, this will reduce the amount of your donation that may qualify for a deduction. You can skip the points back if you want your full donation to support the project that you are donating to.

When donating to a campaign, donors can elect to optionally display their name on the donation leaderboard. This is opt-in; it shows as "Anonymous" by default.

## Supporting Developers

All of the work that we have done to get this website ready is open-source for anyone to use. Developers are free to suggest features, fork our code, and to use our code to run their own campaign websites.

We added [an API endpoint](https://github.com/MAGICGrants/campaign-site?tab=readme-ov-file#funding-required-endpoint) so that developers can easily query information about active and historical campaigns.

## Supporting Our MAGIC Funds and Communities

MAGIC Funds, including the MAGIC Monero Fund and the MAGIC Privacy Guides Fund, are critical in allowing us to pursue our charitable mission. The MAGIC Monero Fund gave us a taste with their initial version of the crowdfunding website of what we could achieve. With this new campaign site, we can support any number of MAGIC Funds, and any number of campaigns per MAGIC Fund.

This wide level of flexibility allows MAGIC Funds to easily pursue new fundraising opportunities that would have been very difficult before.

## What's Next for Our Campaign Website

We love the current state of our campaign site, but there is always room for improvement!

We are still building out the membership program functions. When complete, the campaign site will correctly integrate with [Discourse](https://www.discourse.org/index) so that admins can assign a special flair to users who are members of the MAGIC Fund.

We want to add more perks. If you have suggestions, please [share](mailto:info@magicgrants.org) them with us!

We want to support donations in additional cryptocurrencies. We are exploring the best way to receive Ethereum and ERC-20 token donations.

## A Final Word to Our Donors

To everyone who has supported MAGIC Grants or a MAGIC Fund, ***thank you!*** Your donations allow us to take on big projects like these that benefit our MAGIC Fund communities, our scholarship recipients, and the cryptocurrency public infrastructure that we support.

Would you like to take the new campaign site for a spin by donating to [our 2025 Cryptocurrency Scholarship campaign?](https://donate.magicgrants.org/general/projects/2025-scholarships)
