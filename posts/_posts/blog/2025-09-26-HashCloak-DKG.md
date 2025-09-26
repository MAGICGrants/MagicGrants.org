---
layout: post
title: "HashCloak Writes Security Proofs for Serai's One-Round, Robust Threshold DKG"
excerpt: "MAGIC Grants contracted HashCloak to further substantiate Serai's intended use of an efficient, robust eVRF DKG scheme"
date: 2025-09-26
Author: magicboard
---

MAGIC Grants contracted [HashCloak](https://hashcloak.com/) to write security proofs for the [Serai](https://serai.exchange) project's intended use of a modified [eVRF DKG](https://eprint.iacr.org/2024/397) scheme.

In simple terms, HashCloak provided security proofs for the streamlined communication method proposed by the Serai project. This communication is how Serai nodes ensure they properly create the keys for multisignature wallets with robust properties. With this work, the key generation can efficiently occur with only one round of communication while still preserving security, instead of the two or three rounds that were required before.

Hernán Darío Vanegas Madrigal from HashCloak formalized the non-interactive verifiable encryption scheme. Luke Parker proposed the original scheme.

We would like to thank HashCloak for their efforts to ensure safe communication. We would like to thank Power Up Privacy for their donation that made this review possible.

[Read the Report](https://github.com/serai-dex/serai/blob/next/audits/crypto/dkg/evrf/Security%20Proofs.pdf){: .btn-primary}

[Read Serai's Commentary](https://serai.exchange/2025/09/26/dkg-evrf-security-proofs.html){: .btn-secondary}