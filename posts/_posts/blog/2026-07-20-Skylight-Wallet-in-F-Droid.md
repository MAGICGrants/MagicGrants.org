---
layout: post
title: "Skylight Wallet is Now Available in the Official F-Droid Repository"
excerpt: "Skylight Wallet is the first Monero wallet with zero 'anti-features' in the official F-Droid repository"
date: 2026-07-20
Author: magicboard
---

Skylight Wallet for Monero is now available in the official F-Droid repository! Additionally, Skylight Wallet builds are now fully reproducible.

Skylight Wallet is our open-source and self-custody [light-wallet for Monero](https://skylight.magicgrants.org). Unlike most other self-custody Monero wallets that require significant scanning to be performed on-device, Skylight Wallet connects to a light-wallet server (LWS) that performs the scanning with a view key (but which does not have the permission/ability to spend funds). Since the LWS maintains the status of the wallet, devices can stay fully updated in an instant, even when using our on-by-default Tor connections.

The downside is that users need to select a LWS that they trust to preserve their privacy, such as their own.

Skylight Wallet has been available on [Google Play](https://play.google.com/store/apps/details?id=org.magicgrants.skylight), the [App Store](https://apps.apple.com/us/app/skylight-wallet-for-monero/id6759176050), and [GitHub](https://github.com/magicgrants/skylight-wallet) (including desktop versions); however, it is now available on the ***official*** F-Droid repository as well.

Skylight Wallet does not have any "[anti-features](https://f-droid.org/en/docs/Anti-Features/)," such as ads, non-free dependencies, and tracking. Skylight Wallet is the first Monero wallet on the F-Droid official repository that does not have any anti-features.

[Get Skylight Wallet on F-Droid](https://f-droid.org/en/packages/org.magicgrants.skylight/){: .btn-primary}

[F-Droid](https://f-droid.org) is a distribution ecosystem for free and open-source (FOSS) Android apps. F-Droid’s core mission is to provide a trusted way to find and share privacy-respecting, FOSS apps for Android. For an app to be listed on the F-Droid repository, it must have a FOSS license and meet [other requirements](https://f-droid.org/en/docs/Inclusion_Policy/).

The F-Droid maintainers asked us to make Skylight Wallet reproducible. Skylight Wallet's core code was reproducible prior to us submitting it for consideration; however, the maintainers [challenged us](https://gitlab.com/fdroid/fdroiddata/-/merge_requests/37027#note_3511067884) to make the "monero_c" dependency that Skylight Wallet uses reproducible as well. Previously, "monero_c" was built transparently but not reproducibly. With recent improvements, Skylight Wallet is more reproducible!

Reproducible builds ensure that the code you see on our repository is the code that you run on your device. Reproducible builds do not guarantee that the wallet is bug-free, but they help reduce supply chain risks.

## What's Next for Skylight Wallet

Skylight Wallet is about to support new connection options. In addition to LWS connections, Skylight Wallet will soon support connections to remote nodes with local (on device, no LWS) scanning, which matches the user experience of most other Monero self-custody wallets. You will be able to easily configure which connection type is best for you.

We will also spinoff a new application focused on compatibility with Serai and the assets it supports (Bitcoin, Ethereum, Monero, and Serai). This will allow Skylight Wallet to remain fully Monero-focused. Stay tuned for more details about this spinoff wallet! We hope you are as excited about it as we are.
