---
layout: post
title: "Monero FCMP++ Cryptography Implementation Audited by Trail of Bits"
excerpt: "MAGIC Grants commissioned Trail of Bits to audit a portion of Monero's forthcoming Monero FCMP++ cryptography implementation"
date: 2026-08-17
Author: magicboard
---

MAGIC Grants contracted [Trail of Bits](https://www.trailofbits.com/), a leading cybersecurity and research firm, to audit certain cryptography for Monero's forthcoming FCMP++ upgrade. This upgrade will substantially increase the privacy of Monero transactions.

> FCMP++ is [short for](https://www.getmonero.org/2024/04/27/fcmps.html) "Full Chain Membership Proofs + Spend Authorization + Linkability."

MAGIC Grants has assisted the Monero community with a number of security reviews, both for and outside of the Monero FCMP++ upgrade. Trail of Bits was selected for this project through a competitive bidding process.

The Trail of Bits audit was prepared by Joe Doyle under the direction of Jim Miller, Engineering Director, Application Security and Cryptography.

The review consisted of two engineer-weeks of effort. Doyle's efforts primarily involved reviewing incremental modifications to the Monero cryptography core libraries.

Doyle found that the changes made are focused and appear to be correct, though he suggested a larger test suite and better documentation. **The review produced six informational findings. Zero high, medium, and low-severity findings were discovered.**

Five of these findings have been resolved, and one of these has been partially resolved.

The partially resolved finding concerns fragile memory layout assumptions in a Rust FFI function. Compile-time static assertions have been added to safeguard the FFI interface, though Trail of Bits says that the interface itself remains fragile.

Further information on all six findings and their resolutions are available in the public audit report.

MAGIC Grants would like to thank Trail of Bits for their detailed review of this project, We would like to thank Justin Berman for their efforts in developing Monero and selecting the appropriate audit scope. Finally, we would like to thank the Monero community donors for funding this audit.

[Read the Audit Report](https://github.com/trailofbits/publications/blob/master/reviews/2026-07-magicgrants-monerofcmp++crypto-securityreview.pdf){: .btn-primary}
