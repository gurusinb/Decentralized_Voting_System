## Decentralized Voting System
![Open Source Love svg1](https://badges.frapsoft.com/os/v1/open-source.svg?v=103)
[![Maintenance](https://img.shields.io/badge/Maintained-yes-green.svg)](https://github.com/gurusinb/Decentralized_Voting_System)
[![Maintenance](https://img.shields.io/badge/Deployed-no-red.svg)](https://github.com/gurusinb/Decentralized_Voting_System)

This is a prototype of a Decentralized App(DApp) build using Ethereum
Blockchain Technology <br> which allows voters to vote in an election
using a Distributed Ledger Technology (DLT).

![alt text](https://raw.githubusercontent.com/gurusinb/Decentralized_Voting_System/MASTER/Sample%20Output/img-1.png)

## Why use a DApp for Voting

Problems with the current Voting System
* Cases of vote alteration and manipulation
* Prone to Malware Attacks
* Requires a lot of human resources and time

Advantages of using Blockchain Technology
* Vote anytime / anywhere
* Transactions are secure and immutable
* Fast Transactions with less expenditute
* Transparent

## Installing Dependencies
Following is the list of packages required to run the App

    web3
    solidity
    ganache

Web3 is a 
collection of libraries that allow us to interact with a local or 
remote ethereum node using HTTP, IPC or WebSocket. 

    npm install web3@0.20.1

Solidity is an object-oriented programming language used for writing Smart contracts
on various blockchain platforms, most notably, Ethereum. We can relate Smart contracts
with concept of Abstraction in Object Oriented Programming.
  
    npm install solc@0.4.17

Ganache is a blockchain simulation tool which enables us to develop, deploy, and test
our dApps in a safe and deterministic environment.

    npm install ganache-cli@latest

## Instructions to use the App :

* First clone the repository
  
      $ git clone
      $ cd Decentralized_Voting_System
  
* Open two terminals
* On one terminal run the ganache client
  
      $ node_modules/.bin/ganache-cli
  
* On the other terminal compile and deploy the smart contract
      
      RS7:~/c/Decentralized_Voting_System $ node
      > Web3 = require('web3')
      > web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"))
      > code = fs.readFileSync('Voting.sol').toString()
      > solc = require('solc')
      > compiledCode = solc.compile(code)
      > abiDefinition = JSON.parse(compiledCode.contracts[':Voting'].interface)
      > VotingContract = web3.eth.contract(abiDefinition)
      > byteCode = compiledCode.contracts[':Voting'].bytecode
      > deployedContract = VotingContract.new(['Rama','Nick','Jose'],{data: byteCode, from: web3.eth.accounts[0], gas: 4700000})
      > contractInstance = VotingContract.at(deployedContract.address)
      > deployedContract.address
  
* Change the contract address in index.js to deployedContract.address
* Now one can vote through the node console or by using the Webpage
* Voting from node console
  
      > contractInstance.voteForCandidate('Candidate-Name', {from: web3.eth.accounts[0]})
      > contractInstance.totalVotesFor.call('Candidate-Name')

### Snapshots of the Application
![alt text](https://raw.githubusercontent.com/gurusinb/Decentralized_Voting_System/MASTER/Sample%20Output/img-2.JPG)

