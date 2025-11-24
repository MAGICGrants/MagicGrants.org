---
layout: post
title: "Introducing Skylight Wallet, a Modern Monero Light-Wallet"
excerpt: "Skylight Wallet is an open-source and self-custody light-wallet for Monero"
date: 2025-11-24
Author: magicboard
---

MAGIC Grants is excited to announce [Skylight Wallet](https://skylight.magicgrants.org), a modern, open-source, and self-custody Monero light-wallet.

Skylight Wallet is available today on Android, and it will be available soon on iOS and desktop.

[Google Play](https://play.google.com/store/apps/details?id=org.magicgrants.skylight){: .btn-primary}

[GitHub APK](https://github.com/magicgrants/skylight-wallet){: .btn-secondary}

Skylight Wallet requires a user to provide their own light-wallet server (LWS). We do not operate our own server or provide one by default (we don't want your view keys). If you do not already have a home server, we suggest [reading our guide](https://www.privacyguides.org/articles/2025/06/12/monero-server-using-truenas/) on how to set one up with TrueNAS.

## About Monero Light-Wallets

Unlike conventional Monero wallets, light-wallets outsource wallet scanning to a server (that ideally you run yourself). This has significant performance improvements, including:

* **No on-device syncing.** When you open Skylight Wallet, it will immediately sync all the information you need from the server.

* **Hugely improved Tor performance.** Since minimal information needs to be sent to Skylight Wallet, it's exteremely reasonable to connect over Tor.

* **Better battery performance and lower data consumption.** Let your device relax instead of syncing repeatedly in the background.

* **Sync across devices.** You can have multiple Skylight Wallets connected to one LWS, including multiple devices connected for the same wallet. Everything is synced once on the server, which doesn't need to be repeated on each device.


## App Highlights

* **Open-source.** Skylight Wallet is fully open-source and MIT licensed. Anyone can take our code and further improve it!

* **Self-custody.** You have full controls over you spend keys. Your view keys are only shared with the LWS that you manually specify.

* **Automatic Tor protection.** Without needing to configure anything, Skylight Wallet automatically protects your connections with Tor.

* **OpenAlias sending support.** Easily and securely send to DNS address records.

* **Address book.** Easily pay frequent recipients.

* **Subaddress support.** If your LWS supports subaddresses, Skylight Wallet will display fresh subaddresses.

## Why We Made Skylight Wallet

We made Skylight Wallet because we wanted it, and we think you will benefit from it too. Skylight Wallet will not replace other great Monero wallets, but we felt that we could do a successful take on a modern Monero light-wallet, something that as far as we know had not been attempted. We believe that this will lead to improved Monero user experiences in all wallets.

Having our own wallet means we do not need to wait on anyone else to try out our ideas, including integrations with decentralized exchanges.

## I Have a Question or Feedback

Great! [Check out the Skylight Wallet website FAQ](https://skylight.magicgrants.org).

[Join our Matrix community](https://matrix.to/#/#skylight-wallet:monero.social) to share your feedback with us.

## Special Thanks

We would like to give a special thanks to the following people that helped make this app possible.

* Lee Clagett for their work on Monero LWS and LWSF.
* Czarek and Cake Wallet for their monero_c library.
* Stack Wallet for their Arti/Tor library.

If you would like to contribute to MAGIC Grants, please [consider a donation](https://donate.magicgrants.org/general).
