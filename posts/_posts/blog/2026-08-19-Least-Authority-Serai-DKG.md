---
layout: post
title: "Serai Distributed Key Generation Implementation Audited by Least Authority"
excerpt: "MAGIC Grants commissioned Least Authority to audit Serai's DKG implementation"
date: 2026-08-19
author: magicboard
---

MAGIC Grants contracted [Least Authority](https://leastauthority.com), a leading security research firm, to audit Serai's Distributed Key Generation (DKG) implementation. [Serai](https://serai.exchange) is a forthcoming decentralized exchange that will initially be compatible with the Ethereum, Bitcoin, and Monero blockchains.

Serai is open-source and has a strong potential to be important public infrastructure. Thus, security reviews are essential to ensure the safety of its components.

Serai has been designed to be agnostic to what underlying blockchain technology it uses, and it allows for the ability to migrate to another system later if deemed appropriate. Using Polkadot's Substrate was preferable to designing these blockchain components from scratch.

MAGIC Grants [previously contracted](https://magicgrants.org/2025/09/26/HashCloak-DKG) HashCloak to write the DKG security proofs for the streamlined communication method proposed by the Serai project. This communication is how Serai nodes ensure they properly create the keys for multisignature wallets with robust properties. With this work, the key generation can efficiently occur with only one round of communication while still preserving security, instead of the two or three rounds that were required before.

Least Authority's review was prepared by George Gkitsas, Miguel Quaresma, Burak Atasoy, and Jessy Bissal. Their review occurred over two weeks.

Least Authority identified two low-severity issues that were resolved in [two](https://github.com/serai-dex/serai/commit/4c34222fcee860d720a8f39da0484cea4644f456) [commits](https://github.com/serai-dex/serai/commit/817e81ff5fc9de936cae84dd6220ab51a4f1e234).

MAGIC Grants would like to thank Least Authority for their detailed review of this project, and we would like to thank Luke Parker for their efforts in developing Serai.

[Read the Audit Report](https://leastauthority.com/blog/audit-of-serai-distributed-key-generation/){: .btn-primary}

[Read Serai's Commentary](https://serai.exchange/2026/08/19/dkg-evrf-audit.html){: .btn-secondary}
