---
title: "Monitoring DApp transactions on the backend to enforce business logic"
layout: post
date: 2018-10-01 14:40
image: /assets/images/thumbnails/monitor.png
headerImage: true 
hideTitle: false
wide: false
tag:
- Ethereum
- Geth
- Microservices
- Robust
category: project
subCategory: blockchain
---

<style>
    .center-image{
        margin: 0 auto;
        display: flex;
    }
</style>

## When
Sep 2018 - Oct 2018


## What
Golang microservices that monitor the state of various Ethereum transactions, executing some business logic and updating our cloud firestore based on their status and the resulting state of the blockchain.

## Why
Our (hybrid) DApps core on chain functionality was an escrow system into which one party would deposit funds. Due to the app using [firestore](https://firebase.google.com/docs/firestore/) as a database, it was thus important that its state reflected that of the on chain escrow. Having a pure client side mechanism for managing this state opened up many UX problems, for example: user A sends a tx to our escrow and his browser closes while the tx is pending - in this scenario the data would remain out of sync until either party next attempts to check the state (in addition, we would need to aso create this mechanism which would bloat the UX). We needed some mechanism that maintained high UX while securely enforcing our business rules. 

Benefits of using server:
 - Maintain business logic in one place
 - Provide robustness / mitigate potential security issues
 - Ensure that our corresponding services execute correctly (SendGrid for email notifications)

## How

Tl;dr user sends the transaction to Ethereum > txHash is intercepted and sent for monitoring alongside some contextual info > upon completion/error, resulting smart contract state is read and propagated to dapp/users via database write and email service interaction


![Transaction monitoring architecture]({{ site.url }}/assets/images/blockchain/monitor-architecture.png){: class="center-image" }
<figcaption class="caption">Architecture</figcaption>

1. Escrow deposit transaction is executed via our payment library (utilising web3) and the resulting tx hash is returned and sent to the transaction monitor alongside some contextual information
    - JS Payment library / [web3](https://www.npmjs.com/package/web3)  
2. Transaction monitor receives request from client, saves the transaction details in a SQL table and polls the status of the transaction. When it has been accepted or rejected, we communicate this information forward
    - Microservice on GCP
    - Golang/SQL/(Etherscan/GETH)
3. Receives notification and basic contextual information from the monitor. We can then update the transaction and escrow objects on the database (after retrieving contract state from GETH), and then communicate this information to the users by dispatching emails via SendGrid. 
    - Microservice on GCP
    - Golang/GETH/Firebase/Sendgrid


### Supplementary architecture
In the case of something failing (either in the initial client-server API call, or the server itself, or node sync issue), a 'state-cleaner' endpoint that ensures basic contract state is reflected in the database can be called. In our case, we asynchronously hit this endpoint each time the escrow component is loaded, as a fallback mechanism


### Requirements 
Trustworthy Ethereum node - if it is out of sync (i.e. hasn't received recent blocks) then we will get fed back incorrect information - this is another case of when a fallback mechanism has proven useful 


### Potential improvements
Consolidate functionality and reduce overhead by polling the contract and reverse-engineering the state as opposed to sending the transactions individually/manually to the monitor. In this scenario we would monitor the contract itself (the source of truth), retrieve any new transactions, extract their transaction data and match it up with records in our firebase DB, enforcing the same logic as in the current implementation. In addition, this would allow us to monitor the transactions sent to our contract from other locations


## Links
[Monitor](https://gitlab.com/alsco77/ethereum-transaction-monitor)
[State manager](https://gitlab.com/alsco77/transaction-callback-api)

## Thoughts
- Golang and GCP == awesome








