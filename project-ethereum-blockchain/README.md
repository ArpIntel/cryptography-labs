Ethereum Private Blockchain  Cryptography Implementation Project
Subject: Cryptography  UTS 
Team: Arpitha Srinivasa Murthy & Khelan Prashantbhai Desai 
Tools Used: Geth (Go Ethereum), Genesis.json, Ethereum Console, Linux CLI Topics: Blockchain, ECDSA, Cryptographic Hashing, Digital Signatures, Consensus, Mining

Overview
This project involved setting up and running a private Ethereum blockchain from scratch  configuring the genesis block, running a node, creating accounts, mining tokens, and executing a real transaction between two accounts. The goal was to understand the cryptographic mechanisms that underpin how Ethereum (and blockchain in general) actually works, rather than just using it as an end user.

**Note: This was a group project completed with a partner. My contributions covered the Ethereum node setup, genesis configuration, 
account management, mining, and transaction analysis.**

What We Built
Task 1  Private Ethereum Network Setup
Configured a genesis.json file to define the initial state of the private blockchain  including the chain ID, difficulty, gas limit, and initial account balances. 
Used Geth (Go Ethereum) to initialise the network from this genesis block and launched a node with the JavaScript console enabled for interacting with the chain directly.

Task 2  Account Creation & Mining
Created two Ethereum accounts on the private network and verified their initial balances. Set one account as the etherbase (the mining reward recipient) and began mining  
generating new blocks and accumulating ETH in the base account.

Task 3  Transaction Execution & Analysis
Executed a transaction from the etherbase account to the second account using eth.sendTransaction, then mined it into a block. Retrieved and analysed the full transaction 
object, including:
blockhash  the hash of the block containing the transaction
gas  21,000 wei, the standard cost for an ETH transfer
gasPrice  1,000,000,000 wei (1 gwei)
nonce  0, confirming this was the first transaction from the sender
r and s values  the two components of the ECDSA signature, proving the transaction was authorised by the sender's private key
v  used to recover the sender's public key from the signature
value  the amount of ETH transferred in wei

The Cryptography Behind It
Every Ethereum transaction is signed using ECDSA (Elliptic Curve Digital Signature Algorithm) with the sender's private key. The signature produces the r, s, and v values 
visible in the transaction object. Anyone on the network can use the sender's public key to verify the signature without ever seeing the private key; this is what makes 
trustless transactions possible.
Blocks are linked together via cryptographic hashing; each block contains the hash of the previous block, meaning altering any historical block would invalidate every block 
that follows it. This is the core tamper-resistance property of blockchain.

Key Takeaways
Blockchain is fundamentally applied cryptography  hashing, digital signatures, and public key infrastructure working together at scale
ECDSA signatures in transactions are what make Ethereum trustless  no central authority needed to validate who sent what
Gas and nonces are cryptographic and economic mechanisms that prevent double-spending and replay attacks
Running a private chain is a great way to understand what's actually happening under the hood of public networks like Ethereum mainnet

Skills Demonstrated
Ethereum, Geth, Blockchain, ECDSA, Digital Signatures, Cryptographic Hashing, Smart Contract Infrastructure Genesis Block Configuration, Linux CLI

