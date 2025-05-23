---
layout: post
title: "More Apps for TrueNAS: Monero-LWS, Bitcoin Node, Mempool, and Electrs"
excerpt: "MAGIC Grants publishes additional TrueNAS apps for Monero-LWS, Bitcoin Node, Mempool, and Electrs"
date: 2025-05-23
author: magicboard
---

As part of our efforts to support critical cryptocurrency infrastructure and privacy, MAGIC Grants has implemented additional Monero and Bitcoin apps for TrueNAS. MAGIC Grants has also added major features to the Arti and Monero Node apps.

[TrueNAS](https://www.truenas.com/truenas-community-edition/) is one of the most popular open-source operating systems for network-attached storage (NAS) devices. TrueNAS allows users to install "Apps", which extend the functionality of NAS devices.

Users of TrueNAS can now easily find the following applications on the TrueNAS app store:

* Monero-LWS
* Bitcoin Node
* Mempool
* Electrs

These applications live in the [TrueNAS Apps GitHub repository](https://github.com/truenas/apps) under an open-source license, and anyone can suggest improvements.

We would like to give a special thanks to the TrueNAS Apps repository maintainers (particularly [Stravos Kois](https://github.com/stavros-k)) for reviewing our application submissions, making improvements, and ultimately accepting these apps into their app store.

## Monero-LWS

Monero-LWS allows "lightweight" Monero wallets such as Edge Wallet and MyMonero to offload scanning/syncing needs to this Monero-LWS server. Instead of your wallet needing to sync when you open it, Monero-LWS continuously scans for new transactions in the baackground. Thus, your lightweight Monero wallet is instantly ready to spend without compromising your privacy or consuming your bandwidth.

## Bitcoin Node

You can now easily run a full Bitcoin node on your NAS. Running a Bitcoin node contributes to decentralization and network resilience.

## Mempool

You can self-host your own instance of [mempool.space](https://mempool.space), which is one of the leading block explorers for Bitcoin.

## Electrs

You can connect your Electrum-compatible wallets to your own Electrs server running on your NAS for improved privacy. Don't connect to random Electrum servers; connect to your own!

## Monero Node Improvements

The Monero Node app now fully supports incoming Tor and I2P connections. You can connect to your node over hidden networks and advertise your hidden address to other nodes.

## Arti Improvements

You can now host hidden services with the Arti app, for example to enable incoming connections to your Monero Node or Monero-LWS over Tor.

After adding your hidden services, open the Arti shell and run `arti hss --nickname NICKNAME onion-address` for each to get their onion addresses.

## Support MAGIC Grants

If you find these apps useful, please [consider a donation to one of our active campaigns](https://donate.magicgrants.org/). MAGIC Grants is a 501(c)(3) public charity.
