---
layout: post
title: "Monero FCMP++ Gadgets and Circuit Reviewed by Veridise"
excerpt: "This engagement used formal verification and manual review to ensure the Monero FCMP++ implementation is secure"
date: 2025-08-05
Author: magicboard
---

MAGIC Grants engaged Veridise to conduct a security assessment of several essential components of the forthcoming [Monero FCMP++ upgrade](https://www.getmonero.org/2024/04/27/fcmps.html). The security assessment covered the Monero full-chain membership proof algorithm, arithmetization, and implementation. This circuit proves a Monero output is contained within a publicly known set without revealing any other information.

Veridise conducted the assessment over 12 person-weeks, with 3 security analysts reviewing the project over 4 weeks.

Veridise security analysts reviewed the reports of previous audits for Monero FCMP++, inspected the provided tests, and read the Monero FCMP++ documentation. They then [wrote a translator](https://github.com/Veridise/fcmp-plus-plus/tree/picus/crypto/fcmps/circuit-abstraction) to [Picus](https://github.com/Veridise/Picus), and worked to formally verify determinism of each non-interactive gadget. Next, they began a manual review of the code assisted by automated testing, and formal verification. For full confidence in the soundness of the interactive gadgets, the analysts developed soundness proofs of several components of the protocol. Finally, the analysts developed automated tests to find potential deviations from intended implementation. This effort focused on the Fiat-Shamir transformation, denial-of-service, and privacy violations.

During this review, analysts considered any means by which a potentially dishonest prover could use unexpected or invalid values to produce a valid proof to be a soundness risk to the protocol. On the other side of things, Veridise analysts considered any information which could be abstracted from an honest prover by the verifier to be a privacy risk. The analysts assumed that the prover was executing in a secure environment, and that attackers would not have access to information leaked through side channels. Despite this, the Monero developers (notably Luke Parker) took steps to ensure memory was zeroed out and constant-time operations were used wherever possible.

Veridise found one Warning severity issue and one Information severity issue. Both of these have been addressed.

This review furthers MAGIC Grants's charitable mission to support public payment infrastructure. Thank you to the Monero community for supporting this review.

[Read the Audit Report](https://veridise.com/audits-archive/company/monero-research-lab/magic-grants-monero-fcmp-2025-06-03/){: .btn-primary}

[View the Picus Translator](https://github.com/Veridise/fcmp-plus-plus/tree/picus/crypto/fcmps/circuit-abstraction){: .btn-secondary}
