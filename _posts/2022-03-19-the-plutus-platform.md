---
layout: post 
title: "The Plutus Platform"
date: 2022-03-19 10:39:00 -0000
categories: plutus programming  
---

#### Program-ability in blockchain
When it comes to how widely blockchain technology can be applied to a range of use-cases, it somehow depends on the model a blockchain uses for defining how transactions are settled. 
Bitcoin uses a UTXO model on its ledger. This means that transactions are represented as a series of inputs and outputs that live on the blockchain. The inputs are locked to a pubkey and only the owner of the pubkey can sign the transaction with a corresponding private key in order to unlock those outputs (spending). 
<a href="https://ibb.co/0BsKXCt"><img src="https://i.ibb.co/n3PB07C/Method-Draw-Image-1.png" alt="Method-Draw-Image-1" border="0"></a>
Cardano uses the eUTXO model which extends UTXO by making it possible for the pubkeys that lock outputs to be replaced with small scripts called validators. The validator is deployed as actual script address and lives on the blockchain as an output.
An extra piece of data can be added to a validator and provides the convinience of have extra data in an output without having to modify the validator. This data is referred to as **Datum**. 
<a href="https://ibb.co/HHXbZFZ"><img src="https://i.ibb.co/2k5CJnJ/Method-Draw-Image-2.png" alt="Method-Draw-Image-2" border="0"></a>
For a transaction to spend the value locked on a script address, ie the validator, it needs to provide a few pieces of information:
* **Redeemer:** This is the signature required to unlock the output.
* **Context:** This data that is related to that transaction and it could be anything from the referenced inputs, the outputs such that you can verify that the outputs referenced by the validator actually exist. 

#### The Plutus Platform
The Plutus Platform is a collection of tools such as environment runtime, SDKs and libraries that work together to enable the development Cardano smart contracts. The platform offers a robust way of applications interacting with the Cardano blockchain by abstracting possible areas of complexity from the application developer and applying constraints on how contracts are evaluated. This model attempts to provide assurance that eliminate the risk of loss during transactions. 

It is designed as a set of components that work together: 

* **Plutus Application Framework:** This is a framework designed to  be used for developing client-side Plutus applications. It prodides an SDK and libraries that interface the client application with on-chain smart contract code, wallet front-ends and back-ends, nodes,cli tools etc.
   * **Plutus Application Backend:** The client side runtime for plutus apps. It acts as an intermediary between client side code and the contract code running on the blockchain. 
   * **Plutus Haskell SDK:** It determines how a smart contract is written and how it interacts with the blockchain in a secure, deterministic manner. 

* **Plutus Foundation:** This provide the environment on which on-chain smart contract code can be written. 
   * **Plutus Core**: This is small functional language that smart contract code written compiles into in order to run on the Cardano blockchain. The code could be written in a different language but currently the only supported language is Haskell.
* **Plutus Playground:** Privides a web interface that can be used to write and test basic Plutus applications. It enables visualization on the how a contract is evaluated and setup of different test scenarios.

<a href="https://ibb.co/w0B7hPv"><img src="https://i.ibb.co/0DmKy6w/plutus-platform-architecture.png" alt="plutus-platform-architecture" border="0"></a>

