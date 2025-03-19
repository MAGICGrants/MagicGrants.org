---
layout: post
title: "MAGIC Grants Now Accepts Litecoin and MWEB Donations"
excerpt: "LTC and LTC_MWEB are now accepted programmatically at donate.magicgrants.org"
date: 2025-03-18
author: magicboard
---

MAGIC Grants now accepts Litecoin and Litecoin MWEB (MimbleWimble) donations directly on [our donation website](https://donate.magicgrants.org)!

As far as we know, we are the first registered charity to accept Litecoin MWEB donations with an automated system.

[![Screenshot of Accepting Litecoin MWEB with BTCPay Server](/img/posts/2025-03-18-mweb.png)](/img/posts/2025-03-18-mweb.png)

## About Litecoin

Litecoin is one of the oldest decentralized cryptocurrencies, dating back to 2011. Litecoin is commonly used for its wide exchange accessibility, affordable transactions, and privacy-enhancing MWEB features.

## About Litecoin MWEB

[Litecoin MWEB](https://litecoin.com/learning-center/litecoin-and-mweb-what-it-is-and-how-to-use-it) is a relatively new privacy feature that some Litecoin wallets support.

Litecoin MWEB transactions have a hidden transfer amount, and they usually have greater transaction graph privacy than Litecoin mainnet transactions. However, their privacy is not absolute.

LTC mainnet funds can be trustlessly "pegged" into and out of the MWEB sidechain. The MWEB technology was first proposed for Bitcoin and is also used in Grin.

Litecoin MWEB has limited adoption, and we hope that more merchants accept Litecoin MWEB in the near future. As of March 18, 2025, the LTC balance held in MWEB addresses is 124,000 according to [MWEBExplorer](https://www.mwebexplorer.com/), or about 0.16% of the current LTC supply.

## How the Integration Works

Our donation site is powered by [our open-source code](https://github.com/MAGICGrants/campaign-site/), [BTCPay Server](https://btcpayserver.org/), and the new [Litecoin MWEB Plugin](https://github.com/ltcmweb/btcpayserver-ltcmweb-plugin).

These programs allow us to easily generate unique donation addresses for each checkout experience. **The funds land directly in our own self-custody wallet without the use of any intermediary!**

We then use our [autoforward-autoconvert](https://github.com/MAGICGrants/autoforward-autoconvert) program, which has been expanded to support LTC and MWEB. This allows us to easily convert our received cryptocurrencies to dollars if we desire.

Everything is open-source and self-custody!

## Special Thanks

We would like to thank [Hector Chu](https://github.com/hectorchu) for their extensive efforts on Litecoin MWEB related work. We could not accept Litecoin MWEB at scale without them!

We would like to thank the [Litecoin Foundation](https://litecoin.com/litecoin-foundation) for supporting MWEB.

We would like to thank [Cake Wallet](https://cakewallet.com) and [Seth for Privacy](https://sethforprivacy.com/) for helping to test the MWEB plugin.

## About MAGIC Grants

MAGIC Grants is a 501(c)(3) public charity that supports privacy and cryptocurrency infrastructure. Your donation may qualify for a tax deduction.

MAGIC Grants accepts cryptocurrency and cash donations.

[Donate LTC Today](https://donate.magicgrants.org){: .btn-primary}
