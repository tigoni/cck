---

layout: post
title: "eUTXO in Cardano"
date: 2022-01-15 22:48:00 -0000
categories: cardano blockchain transactions

---
## {{page.title}}

#### Value Transfer
The fundamental function in a blockchain network is to transfer value between parties through transactions. Transactions are propagated through the network, validated and added to the blockchain. Every transaction on the blockchain is open to the network and can be used as proof of value transfer having taken place. 

#### UTXO and Account Balance Blockchains
At present, there are two main accounting models of how transactions take place in blockchains. There is the UTXO model and the account based model. To better understand how transactions work in blockchain in this article, we use an example of Alice buying a book from Bob.
Bitcoin uses the UTXO model which resembles cash transactions. Using the book example where Alice buys from Bob, if Alice had one bitcoin and decides to pay for the book using bitcoin, the wallet she uses selects any unspent bitcoin (inputs) and creates a transaction of the required value (outputs) which is tied to Bob's address. The output in broadcast over the network and added to the blockchain. It is these outputs that are locked to Bob's address that are referred to Unspent Transaction Outputs (UTXO). Similarly, if Bob were to spend that bitcoin,his wallet would consume the UTXO and create new UTXO locked to the receiving address. In UTXOmodel, the smallest unit that can be transacted is a single UTXO and if it happens to have a larger value than what is to be spent, then a change UTXO is created and sent back to the spending wallet. In this way UTXO resembeles transacting in cash.

The other accounting model used for transactions is called the account balance model which is similar to how the banking system works. In this model, Alice paying for the book means that her account balance in the global ledger is updated to deduct the amount while that of Bob who is receiving the payment is credited with the amount. With an account balance block chain, assets are represented as account balances within the user's account and it is this balance which is updated during transactions. Ethereum is an example of a blockchain that uses this model.

#### eUTXO in Cardano
Cardano uses both UTXO and account balance models and therefore the term extended UTXO. With bitcoin the use of UTXO significantly reduces programmability and therefore use-case application is largely constrained to payments. The account balance model as used in Ethereum allows for more programmability but in the process, the semantics of the code are more complex therefore introducing the possibility of errors in the smart contract code. Cardano extends UTXO by allowing for more data in the outputs other than just value. It also adds more logic to the output which determines the condtions under which the transaction can be unlocked. This logic is in the form of scripts. This scripts look at the data and determine if the output can be spent or not. By combining the input and output approach in UTXO and scripts from the account-balance models, Cardano is able to serve more diverse use cases that require programmability while also providing the robustness of the UTXO model. 

