---
layout: post
title: "Lee Clagett Raises Funds to Develop Monero for 3 Months"
excerpt: "This development work will improve security, performance, and usability with an end goal of helping to broaden the user base."
date: 2024-02-20
author: magicboard
---

We are excited that the MAGIC Monero Fund campaign to raise funds for three months of Monero development was successful! We raised $28,800 from 43 donations.

[Link to the campaign](https://monerofund.org/projects/Q1Q2_2024_dev_vtnerd)

vtnerd (Lee Clagett) is the author of [Monero-LWS](https://github.com/vtnerd/monero-lws), and has been a [contributor to the Monero codebase since 2016](https://github.com/monero-project/monero/pulls?page=7&q=is%3Apr+author%3Avtnerd+created%3A%3E2016-10-01). He is a veteran of four CCS proposals; [[1]](https://ccs.getmonero.org/proposals/vtnerd-tor-tx-broadcasting.html), [[2]](https://ccs.getmonero.org/proposals/vtnerd-2020-q4.html), [[3]](https://ccs.getmonero.org/proposals/vtnerd-2021-q1.html), [[4]](https://ccs.getmonero.org/proposals/vtnerd-2023-q3.html)

This proposal funds 480 hours of work, ~3 months. The milestones will be hour based; 160 (1 month), 320 (2 months), 480 (3 months). At the completion of hours, he will provide the Monero Fund committee references to the work that was completed during that timeframe. 

Some features that are being targeted in [`monero-project/monero`](https://www.github.com/monero-project/monero):

* Get new serialization routine merged (work on piecemeal PRs for reviewers sake) (already in-progress)
* Complete work necessary to merge DANE/TLSA in wallet2/epee.
* Adding trust-on-first-use support to wallet2

Work targeted towards [`vtnerd/monero-lws`](https://github.com/vtnerd/monero-lws): 

* Optional full chain verification for malicious daemon attack (already-in progress)
* Webhooks/ZMQ-PUB support for tx sending (watch for unexpected sends)
* ZMQ-pub support for incoming transactions and blocks (notifies of any new transaction or block) 
* Implement "horizontal" scaling of account scanning (transfer account info via zmq to another process for scanning) 
* Make account creation more "enterprise grade" (currently scanning engine re-starts on every new account creation, and uses non-cacheable memory) * Unit tests for REST-API
* Create frontend LWS C/C++ library 
* Provide official LWS docker-image 
* Provide official snap/flatpak/appimge (tbd one or all of those) 
* Provide pre-built binaries 
* (Unlikely) - reproducible builds so community members can verify+sign the binary hashes
* It is unlikely that all features will be implemented, at which point the unfinished features will roll into the next quarter.

Please keep an eye on [MoneroFund.org](https://monerofund.org) for future campaigns, or if you would like to make a donation today to support the MAGIC Monero Fund.
