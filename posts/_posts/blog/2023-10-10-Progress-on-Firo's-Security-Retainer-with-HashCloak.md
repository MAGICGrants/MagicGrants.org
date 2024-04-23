---
layout: post
title: "Progress on Firo's Security Retainer with HashCloak"
excerpt: "Firo fuzz tests have significantly greater coverage, and HashCloak identified security issues with Lelantus Spark and suggested fixes."
date: 2023-10-10
author: magicboard
---

We're pleased to provide an update on our ongoing [security retainer with HashCloak](https://magicgrants.org/Security-Retainer-with-HashCloak/) that was funded from the [MAGIC Firo Fund](/funds/firo/). We'd like to share some of the milestones achieved during this period.

## Improved Fuzzing Code Coverage

[HashCloak](https://hashcloak.com/)'s primary objective has been improving [Firo](https://firo.org)’s fuzzing code coverage, and we're pleased to report considerable progress in this area:

| File                | Previous Coverage (%) | Current Coverage (%) |
|---------------------|-----------------------|----------------------|
| aead.cpp            | 31                    | 95.0%                |
| bech32.cpp          | 7%                    | 90.1%                |
| bpplus.cpp          | 6%                    | 93.5%                |
| chaum.cpp           | 3%                    | 48.5%                |
| coin.cpp            | 7%                    | 51.5%                |
| f4grumble.cpp       | 9%                    | 96.2%                |
| grootle.cpp         | 0.8%                  | 90.7%                |
| mint_transaction.cpp| 0%                    | 40.5%                |
| schnorr.cpp         | 0%                    | 96.5%                |
| spend_transaction.cpp | 0%                  | 14.0%                |

## Review of Pull Requests

1. HashCloak reviewed a proposal related to updating Lelantus Spark's linking tag structure that was intended to allow more flexible membership proof upgrading options. Their review identified a potential flaw in the proposed modification, leading to the withdrawal of the change. [Review the PR here](https://github.com/firoorg/firo/pull/1267).

2. HashCloak team also conducted thorough evaluations on two other PRs addressing a glitch in the Lelantus state change and a Spark runaway exception. They proposed modifications to both and are currently working with the Firo Core Team on these.

## Moving Forward

Due to HashCloak's strong progress and the remaining amount of work, MAGIC Grants is extending the security retainer for at least one more month. We look forward to continuing our security retainer with HashCloak to further increase fuzzing code coverage and review any critical pull requests, especially with the upcoming launch of Firo’s new privacy protocol Lelantus Spark on mainnet.

We would like to extend special thanks to Reuben Yap of the Firo Core Team for facilitating this and the generous donations from the Firo community that made this possible.
