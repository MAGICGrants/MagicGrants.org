---
layout: post
title: "zkSecurity Reviews Generalized Bulletproofs and Publishes a Lean Proof of Its Security"
excerpt: "zkSecurity reviewed the Generalized Bulletproofs code used in Monero's FCMP++ upgrade, wrote a new soundness proof, and later published a machine-checked proof in Lean."
date: 2026-11-12
author: magicboard
---

Back in June, MAGIC Grants contracted [zkSecurity](https://zksecurity.xyz/), a leading research firm, to review the `generalized-bulletproofs` crate inside the `monero-oxide` project, commit `f3660043e042b5608fc9c8ce1383cee238da9d0a`. This code is slated to be used in the Monero [FCMP++ upgrade](https://www.getmonero.org/2024/04/27/fcmps.html).

Generalized Bulletproofs were initially alluded to in [a Curve Trees paper](https://eprint.iacr.org/2022/756) by Matteo Campanelli, Mathias Hall-Andersen, and Simon Holmgaard Kamp. A sketch for "Generalized Bulletproofs" was shared [on GitHub](https://github.com/simonkamp/curve-trees/blob/main/bulletproofs/generalized-bulletproofs.md). This modification to the original Bulletproofs proving system is necessary to accommodate Pedersen vector commitments.

Aaron Feickert (then at Cypher Stack) [expanded the sketch](https://github.com/cypherstack/generalized-bulletproofs) into a full description with security proofs. Brandon Goodell (Cypher Stack) later identified issues with that proof and [proposed fixes](https://github.com/cypherstack/generalized-bulletproofs-fix/).

Luke Parker and Justin Ehrenhofer recorded [episode one of Plaintext](https://www.youtube.com/watch?v=EckeY4TsNkU) on Generalized Bulletproofs in May 2026, shortly before zkSecurity's review began.

zkSecurity reviewed the code alongside the cryptography over ten working days. They wrote a new proof that the protocol is sound (knowledge soundness). The review was carried out by Mathias Hall-Andersen (one of the Curve Trees authors) and Suneal Gong. They found no high or medium severity issues, along with four low and three informational findings. The `monero-oxide` developers have since [responded to](https://github.com/monero-oxide/monero-oxide/commit/31c26d96eaadbba910ffe3613ad8b4cf9c598a93) each of them.

On their own initiative, zkSecurity then wrote a separate proof of the protocol's security in the Lean theorem prover, where every step is checked by machine, and published it in a [public repository](https://github.com/zksecurity/bulletproofs-formal-verification). It proves (with an independent formalization, not a line-by-line check of the proof in the written report) that the Generalized Bulletproofs protocol, in the form Monero implements it, is complete, zero-knowledge, and sound. It also covers two slightly more efficient variants that Monero does not currently use and has no immediate plans to adopt.

As with any formal verification, the scope matters. The Lean proof covers the interactive protocol in an abstract mathematical group. It does not cover the non-interactive (Fiat-Shamir) version that Monero uses, the Rust implementation itself, the specific curves FCMP++ uses, or the FCMP++ circuits built on top of Generalized Bulletproofs. Those parts rely instead on zkSecurity's written proofs and code review (and on [other](https://magicgrants.org/2026/08/17/Monero-FCMP-Cryptography-Implementation-ToB.html) [audits](https://magicgrants.org/2025/08/05/Veridise-Gadgets-Circuit.html) of FCMP++).

MAGIC Grants would like to thank zkSecurity for their detailed review and for the additional work of formalizing the protocol in Lean.

[Read the Audit Report](https://reports.zksecurity.xyz/reports/generalized-bulletproofs/){: .btn-primary}

[PDF Version](https://magicgrants.org/files/2026-06-01-zksecurity-generalized-bulletproofs.pdf){: .btn-secondary}
