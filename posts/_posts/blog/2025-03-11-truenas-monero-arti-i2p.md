---
layout: post
title: "Monero, Arti, and I2P Apps for TrueNAS Scale"
excerpt: "MAGIC Grants publishes Monero, Arti, and I2P apps for TrueNAS Scale"
date: 2025-03-11
author: magicboard
---

As part of our efforts to support critical cryptocurrency infrastructure and privacy, MAGIC Grants has implemented Monero, Arti, and I2P apps for TrueNAS Scale.

[TrueNAS Scale](https://www.truenas.com/truenas-scale/) is one of the most popular open-source operating systems for network-attached storage (NAS) devices. TrueNAS Scale allows users to install "Apps", which extend the functionality of NAS devices.

Users of TrueNAS Scale can now easily find the following applications on the TrueNAS app store:

* Monero Node
* Monero Wallet RPC
* Arti
* I2P

These applications live in the [TrueNAS Apps GitHub repository](https://github.com/truenas/apps) under an open-source license, and anyone can suggest improvements.

We would like to give a special thanks to the TrueNAS Apps repository maintainers (particularly [Stravos Kois](https://github.com/stavros-k)) for reviewing our application submissions, making improvements, and ultimately accepting these apps into their app store. We would also like to thank Seth for Privacy for their [Monero Docker images](https://github.com/sethforprivacy/simple-monerod-docker).

## Monero Node

The Monero Node app allows users to easily install and run a Monero Node (monerod) on their NAS. The app can be configured directly from its user interface to connect to other nodes on the Tor and I2P networks, expose certain P2P and RPC ports for external access, and to choose the blockchain storage location.

Monero users receive significant privacy benefits when using their own node instead of a third-party node. Further, using a trusted node unlocks performance improvements.

If you wish to remotely sync your wallets to your node, we strongly suggest setting up TLS with the Nginx Proxy Manager app. It is unwise to use the RPC commands over an unencrypted connection.

Future versions of this app will allow easy configuration of incoming Tor and I2P RPC connections.

## Monero Wallet RPC

The Monero Wallet RPC app is aimed at advanced users who wish to programmatically use their Monero wallet. This could be useful when combined with other services.

## Arti

[Arti](https://tpo.pages.torproject.net/core/arti/) is an experimental [Tor](https://www.torproject.org/) implementation written in Rust, and it is designed to be modular, reusable, and easy to audit. As far as we know, this is the first major deployment of Arti [on Docker](https://github.com/MAGICGrants/arti-docker).

Arti is still in active development, and its developers do not recommend using Arti for any sensitive tasks. [Cuprate](https://github.com/Cuprate/cuprate), a Monero node written in Rust, also [plans](https://repo.getmonero.org/monero-project/ccs-proposals/-/merge_requests/564) to use Arti.

Future versions of this app will allow easy configuration of hosted onion services, such as hosting the Monero Node RPC at an onion address.

## I2P

[I2P](https://geti2p.net) is an anonymizing network, offering a simple layer that identity-sensitive applications can use to securely communicate. This app uses the [Java implementation](https://github.com/i2p/i2p.i2p) of I2P.

Future versions of this app will allow easy configuration of hosted hidden services, such as hosting the Monero Node RPC at an I2P address.

## Looking Ahead

MAGIC Grants is interested in maintaining these apps for the foreseeable future. Above that, our primary goals are:

* More apps, including Monero-LWS and Bitcoind.
* More features, including easier operation of onion/hidden services.

If you have any suggestions and would like to get involved, please contact us at <info@magicgrants.org>.
