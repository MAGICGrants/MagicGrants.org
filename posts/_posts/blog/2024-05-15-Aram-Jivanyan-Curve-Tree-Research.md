---
layout: post
title: "Aram Jivanyan Publishes Research on Lelantus Spark with Curve Trees"
excerpt: "Aram Jivanyan's research into curve trees allows for more efficient private transactions on Firo"
date: 2024-05-15
author: magicboard
---

Aram Jivanyan, a researcher with years of research and implementation experience with Firo and Lelantus Spark, [has published](https://firo.org/about/research/papers/Lelantus_Sparks_with_Curve_Trees__Implementation_Notes.pdf) the research results from his work. Aram [was supported](/2023/05/24/Aram-Jivanyan-to-Research-Firo-Curves) by the [MAGIC Firo Fund](/funds/firo).

[Read the Research](https://firo.org/about/research/papers/Lelantus_Sparks_with_Curve_Trees__Implementation_Notes.pdf){: .btn-secondary}

[![Firo Curve Trees: Global Anonymity Sets for Lelantus Spark](/img/posts/2024-05-15-aram-jivanyan-curve-tree-research.png)](/img/posts/2024-05-15-aram-jivanyan-curve-tree-research.png)

[Curve trees](https://eprint.iacr.org/2022/756) is a new technique that allows scaling zero-knowledge membership proofs to allow global anonymity sets, meaning that the ZKP is performant enough that it can encompass all transactions in a blockchain. It achieves this without any need for a trusted setup, a key requirement of Firo’s privacy research, while retaining small transaction sizes and quick proving and verification times. Curve trees also allow for efficient batching verification techniques, which can further decrease the marginal cost of proof verification. Lelantus Spark’s modular design allows the upgrading of its components, and in this case, curve trees would replace Spark’s use of [one-out-of-many proofs](https://eprint.iacr.org/2014/764.pdf). The research note covers the necessary modifications to implement curve trees in Spark to scale it to global anonymity sets.

We would like to thank Aram Jivanyan for their work, and we would like to thank Luke Parker and Aaron Feickert for their support and feedback during the research process.

### About Firo

[Firo](https://firo.org) is a privacy-preserving blockchain that seeks to protect users’ financial privacy. Its core team is behind the protocol design and implementation of the Lelantus and Lelantus Spark privacy protocols. Formerly known as Zcoin, it has also implemented various privacy-preserving protocols over its existence, leveraging discrete-log based zero-knowledge primitives. Further, they provided the anonymous voting infrastructure for the Thai Democrat Party elections in 2018.

### About MAGIC Grants

MAGIC Grants is a 501(c)(3) public charity that supports cryptocurrency networks, which are essential public payment infrastructure. MAGIC Grants empowers communities to set up MAGIC Funds for various projects deemed essential. These Funds are semi-autonomous and can choose to fund various qualifying activities, including educational materials, essential developer maintenance, research, and security audits.

### About MAGIC Firo Fund

The [MAGIC Firo Fund](/funds/firo) was established in December 2022 and is administered by the MAGIC Board independently from the Firo Core team. The MAGIC Firo Fund is funded by generous donations from Firo supporters. Donations to the fund are tax deductible for US individuals and businesses.
