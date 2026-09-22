---
layout: post
title: "Bulletproofs+ Aggregate Range Proof Issue Identified and Resolved"
excerpt: "MAGIC Grants commissioned Dr. Wang and Dr. Liu for an independent security review of the Bulletproofs+ aggregate range proof after an issue was identified"
date: 2026-09-22
author: magicboard
---

While Dr. Nan Wang and Dr. Dongxi Liu were working on [their project](https://donate.magicgrants.org/monero/projects/2026-range-proofs-speedup) with the MAGIC Monero Fund to identify more efficient zero-knowledge range proofs for Monero, Dr. Wang contacted MAGIC Grants to share that he had identified an issue with the Bulletproofs+ aggregate range proofs. This was a major concern, because the [Monero network deployed](https://www.getmonero.org/2022/04/20/network-upgrade-july-2022.html) Bulletproofs+ in August 2022.

Within minutes, MAGIC Grants hosted a remediation call with Monero researchers and developers, including Luke Parker and Dr. Brandon Goodell from Cypher Stack.

The MAGIC Grants board of directors immediately approved an expanded research contract for Dr. Wang and Dr. Liu to independently review the suitability of Monero's use of Bulletproofs+. Simultaneously, we evaluated possible "worst case" scenarios to determine the required remediation steps should Monero's use have been deemed unsafe.

We are pleased that after their review, which includes new security proofs, ***the Monero network is not vulnerable*** as a result of the issues identified with the original Bulletproofs+ aggregate range proofs.

MAGIC Grants is grateful to the MAGIC Monero Fund for commissioning the initial research project that led to the identified issue, we are grateful to Dr. Wang for identifying and raising the issue, and we are grateful to Luke Parker and Dr. Goodell for their help in triaging this issue.

This serves as an important reminder that everything deployed to the Monero network needs to be reviewed with a high degree of scrutiny. Bulletproofs+ [were audited](https://suyash67.github.io/homepage/assets/pdfs/bulletproofs_plus_audit_report_v1.1.pdf), and this audit noticed a problem in the same proof. However, the reviewers did not fully write out the steps to repair the proof; they instead simply said "the result follows." For critical code deployed to the Monero network, these proofs should be fully written out so that they can better withstand academic scrutiny.

We are publicly sharing this preprint report, which you can read using the link below.

We are also pleased to announce that Dr. Wang, Dr. Liu, Dr. Goodell, and other members of the Cypher Stack team are collaborating with the intent to create a combined, improved paper that includes formal verification. When complete, we will link to that updated version as well.

[Read the Report](/files/2026-09-22-bulletproofs+-report.pdf){: .btn-primary}
