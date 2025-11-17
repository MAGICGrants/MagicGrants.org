---
layout: post
title: "Monero Node RPC Endpoints Now Have 100% Fuzzing Coverage"
excerpt: "The MAGIC Monero Fund worked with ADA Logics to add OSS-Fuzz fuzzing to the Monero Node RPC endpoints"
date: 2025-11-17
Author: magicmonerofund
---

The MAGIC Monero Fund contracted [ADA Logics](https://adalogics.com/) to provide fuzzing coverage in OSS-Fuzz for the Monero Node [RPC endpoints](https://github.com/monero-project/monero/tree/master/src/rpc).

Thank you to the donors who contributed to our [fundraising campaign](https://donate.magicgrants.org/monero/projects/fuzzing-monero-rpc)!

## Proposal Summary

We observed that the most commonly reported vulnerabilities to the [Monero HackerOne program](https://hackerone.com/monero?type=team) were related to RPC vulnerabilities affecting the availability of nodes.

This proposal sought a more proactive approach to catch these vulnerabilities before they were reported or exploited. We focused this initial project on the most exposed component: the Monero Node RPC endpoints. Any RPC vulnerabilities discovered could be exploited remotely.

## Deliverables

ADA Logics submitted a [pull request](https://github.com/monero-project/monero/pull/10004) to the Monero repository adding RPC fuzzing harnesses.

ADA Logics created an [end-to-end Python-based fuzzing harness](https://github.com/AdaLogics/monero-e2e-fuzzing) to target a live Monero daemon.

ADA Logics produced a written report detailing their efforts in creating the harnesses.

[Read the Report](/files/2025-08-17-monero-fuzzing-audit-report.pdf){: .btn-primary}

## Fuzzing Harness Findings

During the engagement, three findings were discovered and responsibly reported to the Monero developers via HackerOne.

- The first finding triggered a stack-based buffer overflow.

- The second finding triggered the Monero daemon to crash upon receiving a specially crafted RPC request.

- The third finding triggered a soft restart of the daemon via a restricted RPC endpoint.

We appreciate the Monero developers' quick response in deploying fixes to address these vulnerabilities.

## Continuous Scanning

ADA Logics improved the Monero tests and configured [Google's OSS-Fuzz](https://github.com/google/oss-fuzz) to regularly test the Monero Node RPC endpoints. The improvements increased the overall code coverage to [roughly 22%](https://introspector.oss-fuzz.com/project-profile?project=monero), which is a substantial increase from the 10% coverage that existed before this project. These harnesses will continuously be fuzzed as new code is merged with large amounts of compute donated by the Google OSS-Fuzz team.

[![Screenshot of Fuzzing Coverage Chart](/img/posts/2025-11-17-fuzzing-chart.png)](/img/posts/2025-11-17-fuzzing-chart.png)


## Next Steps

We aim to further improve Monero's fuzzing coverage where it is reasonable to do so. Our immediate targets include crypto, p2p and the new fcmp++ code.
