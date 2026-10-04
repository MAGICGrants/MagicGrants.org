---
layout: post
title: "Skylight Wallet's Redesign"
excerpt: "Skylight Wallet release 2.0.0 has been completely redesigned to support many new features"
date: 2026-10-04
author: magicboard
---

[![Skylight Wallet 2.0.0 feature graphic showing the redesigned connection settings, home, and address book screens](/img/posts/2026-10-04-skylight-wallet-v2.png)](/img/posts/2026-10-04-skylight-wallet-v2.png)

Skylight Wallet for Monero, our free, open-source, and self-custody wallet, has now been completely redesigned with a modern interface and many new features!

Skylight Wallet was the [first modern Monero light-wallet](https://magicgrants.org/2025/11/24/Introducing-Skylight-Wallet) that allowed you to easily connect to your own light-wallet server (LWS). With Skylight Wallet 2.0.0 and 2.1.0, you can continue using your LWS or choose to connect to a Monero node. This is how most other Monero wallets connect.

Thus, you no longer need to use a Monero LWS to use Skylight Wallet.


## A Fresh Design

[![Skylight Wallet home screen in the dark theme](/img/posts/2026-10-04-skylight-wallet-v2-home-dark.png)](/img/posts/2026-10-04-skylight-wallet-v2-home-dark.png)
[![Skylight Wallet connection settings with light-wallet server and Monero node options](/img/posts/2026-10-04-skylight-wallet-v2-connection.png)](/img/posts/2026-10-04-skylight-wallet-v2-connection.png)
[![Skylight Wallet Tor settings with built-in Tor, external Tor, and no Tor options](/img/posts/2026-10-04-skylight-wallet-v2-tor.png)](/img/posts/2026-10-04-skylight-wallet-v2-tor.png)
[![Skylight Wallet address book with saved contacts](/img/posts/2026-10-04-skylight-wallet-v2-address-book.png)](/img/posts/2026-10-04-skylight-wallet-v2-address-book.png)
{: .screenshots}

Skylight Wallet now has a beautiful and fresh design to match its modern capabilities. Navigation is clearer and more consistent, and settings are better grouped.

Skylight Wallet now supports both dark and bright themes!

## Background Syncing

Skylight Wallet supports background syncing on both Android and iOS with incoming transaction notifications.

When Skylight Wallet is configured in LWS mode, Skylight Wallet will periodically check for new information from the LWS. This supports both Tor and clearnet connections, but iOS users may notice delayed notifications with Tor.

When Skylight Wallet is configured in remote node mode, Android users can choose to have the application only scan when least intrusive or continuously scan all the time. Background scanning in remote node mode is not supported on iOS.

## OpenAlias V2 Over Tor

Skylight Wallet now supports sending to users with second-generation OpenAlias records. Like the original OpenAlias specification, OpenAlias V2 allows users to save their addresses into DNS records, which wallets can fetch. This makes it easy to securely send funds to a human-readable name while using the same infrastructure that powers the rest of the internet.

OpenAlias V2 expands on the original specification by adding more flexible (and optional) metadata fields, separating assets from blockchains, and adding priorities to allow for more complex logic. The benefits are most profound for assets on multiple blockchains.

Skylight Wallet currently only fetches OpenAlias addresses over Tor, so if you have Tor disabled, then OpenAlias lookups will not work. In a future update, we will allow you to lookup OpenAlias records over the clearnet if desired.

## Desktop in Alpha

Skylight Wallet also has a redesigned desktop experience in alpha. If you want to tinker, now is a great time to check that out. If you want a stable experience, consider waiting for a later desktop release.

## What's Next

We teased last time that we would make another wallet, and that will be announced imminently. We will also continue working on the Skylight Wallet desktop and other features that the community wants. Please make your voice heard [in our Matrix community](https://matrix.to/#/#skylight-wallet:monero.social)!


[Download Skylight Wallet](https://skylight.magicgrants.org){: .btn-primary}
[Desktop Alpha Releases](https://github.com/MAGICGrants/skylight-wallet/releases){: .btn-secondary}
