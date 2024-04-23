---
layout: post
title: "Aram Jivanyan to Research Elliptic Curves"
excerpt: "Aram Jivanyan is working on improving Lelantus Spark, with an aim to get anonymity sets in the millions"
date: 2023-05-24
author: magicboard
---

Aram Jivanyan, a researcher with years of research and implementation experience with Firo and Lelantus Spark, is working with MAGIC Grants to conduct six months of additional curve research to improve the privacy of Lelantus Spark.

This research grant was made possible because of the [generous donation](https://magicgrants.org/200000-Donation-from-Arcadia-for-Firo/) to the [MAGIC Firo Fund](/funds/firo/) by [Arcadia](https://www.arcadiamgroup.com/).

Before working with MAGIC Grants, Aram did preliminary work to assess the feasibility of this research direction. Following this initial analysis, he is confident that this research project is likely to bring greater anonymity sets to the final Lelantus Spark implementation.

The aim of the further 6-month research is the following:

1. Research the most efficient path forward for implementing paired elliptic curve (relating to secP256k1, secQ256k1, and/or other applicable curves). One direction will be implementation of the curve on C++ based on the existing curve implementation. Another possible direction can be bindings of Rust implementation into our C++ library.

2. Nail down how the membership proofs with curve trees will be integrated into the full lelantus spark design and what should be modified to make them interoperable with other spark components.

3. Design the bulletproof-based circuit for set membership checks and nail the implementation details for coding.

4. Write a new paper which will summarizes all research, findings and design for enabling Scaling Lelantus Spark Anonymity Set with Curve Trees.

The research aims to solve the greatest challenge of Spark which is enabling anonymity sets in the millions. Other privacy cryptocurrency protocols such as Monero's Seraphis could potentially benefit of this research as well.

The funding will also cover the Aram's continuing research on the [Aura voting protocol](https://eprint.iacr.org/2022/543) to improve the paper, work on the implementation design and architecture and improve the preprint to get it submitted to crypto conferences.

Stay updated with the MAGIC Grants and Firo social media accounts for updates on this research project.
