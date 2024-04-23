---
layout: post
title: "MAGIC Grants-Funded Research Paper on Monero Ring Signature Resiliency to AI Analysis Published"
excerpt: "The research was completed over six months and used artificial intelligence to test the strength of ring signatures absent external information, with modest results."
date: 2022-09-13
author: magicboard
---

MAGIC Grants and the [MAGIC Monero Fund](/funds/monero) are extremely pleased to announce the final research paper by ACK-J on Monero ring signatures. ACK-J created a series of Monero transactions using different spend patterns and applied artificial intelligence models to determine the resiliency of ring signatures against these models absent external information.

The full paper entitled "Lord of the Rings: An Empirical Analysis of Monero's Ring Signature Resilience to Artifically Intelligent Attacks" is available [on the author's GitHub](https://raw.githubusercontent.com/ACK-J/Monero-Dataset-Pipeline/main/Lord_of_the_Rings__An_Empirical_Analysis_of_Monero_s_Ring_Signature_Resilience_to_Artificially_Intelligent_Attacks.pdf), along with [the accompanying dataset pipeline](https://github.com/ACK-J/Monero-Dataset-Pipeline).

This research was funded by the [MAGIC Monero Fund](/funds/monero). It is the first research paper funded through MAGIC Grants.

Justin Ehrenhofer of the MAGIC Grants board messaged the author with a series of questions about the paper. These questions and ACK-J's answers are listed below:

## What inspired you to work on this research project?

Quality datasets are a key component of data science; however, they are notoriously difficult to collect. While the Monero blockchain is public, common metadata such as the transaction amount, sender, and receiver are kept private. With no previous datasets available, there was a blindspot where data scientists couldn't corroborate Monero's privacy guarantees. Monero obfuscating or encrypting most metadata for privacy reasons makes collecting this data an interesting challenge. Initially, I saw other researchers frustrated with the lack of available datasets. I've worked on similar machine learning research in the past, and I thought this would be the best way I could help contribute my skills to Monero. 

## Can you summarize the data collection and analysis processes for a layperson?

Since no previous datasets were available to data scientists and security researchers to study Monero, I made a pipeline to automate Monero transactions between wallets and extract the transaction information into a cleaned dataset. Data scientists can use these datasets to understand if any implementation errors hurt user privacy. The analysis of the transactions uses a form of "pattern recognition" to determine which pieces of public information can hint at the "true spend." Since I was the sender for all the transactions, the dataset could include private information such as the transaction amount, "true spend" position, and wallet addresses. 

## Can you summarize the results for a layperson?

The results showed that with 11 ring members, public information on the monero could aid an attacker in predicting the true spend of a transaction greater than the random guessing probability of 9% (1/11). With this model, the likelihood of a correct guess grew to 13.3%, a modest increase. Since the data was collected, Monero increased its ring size to 16; thus, the accuracy should now be lower, but I do not have numbers for this.

## The data was trained using stagenet data that you collected. In your opinion, is there a large likelihood of the stagenet data being relevant to mainnet data?

The data collection was conducted on the stagenet for multiple reasons. Since the dataset was going to be published publicly, using real mainnet transactions would have privacy implications for other users. These testing networks have transaction patterns that largely differ from the main network. The research results showed models predicted on the stagenet dataset with a 34.6% accuracy compared to a 13.3% on mainnet. However, even with different transaction patterns, the models were able to beat the random guessing threshold on mainnet transactions, indicating a small but significant crossover.

## What steps did you take to make the data as relevant to mainnet transactions as possible? What factors would make the data more or less relevant?

This was a major focus of my research, and I did lots of experiments to create the most realistic dataset possible. The three main enhancements to simulate real users included altering the transaction fees, altering the amount spent, and forcing wallets to sleep in between subsequent transactions mimicking user behavior. This broke up TXO's within each wallet into unpredictable amounts, altering the number of ins to each transaction. 

## What else can be investigated from the data you collected? What research can build upon your results?

A lot can be done using the datasets released as they include the full gambit of information relating to Monero transactions. The models were all trained via supervised learning; future research could use unsupervised learning to cluster non-standard features such as wallet fee levels. Another research topic that can be tackled using this dataset is identifying how many transactions an adversary needs to spam the network to eliminate decoys. Since I was mainly the only person using the testing and staging networks during this time, 99% of the transactions are deanonymized in the dataset I released. Outside of research, these datasets can be analyzed for educational purposes to visualize what a transaction is composed of as well as the public information available relating to the transaction. 

## Did you have a positive experience working with MAGIC Grants on this project? What did we do well, and how can we improve?

I had a great experience with being funded through the MAGIC Monero fund. The committee members were flexible when I needed extra time for writing, and the payouts were always on time. I highly recommend this avenue for other researchers looking to work on Monero.
