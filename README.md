# Writing Market
A decentralized app for buying and selling articles and essays

## Problem
Writers who want to make money by being paid directly by their readers are at the mercy of centralized tech platforms (e.g. SubStack) which can censor or demonetize them

## Solution
A platform where writers can sell their short essays and articles directly to readers without worrying about censorship

## Architecture
- A smart contract that acts as an escrow -- once it has payment from the reader and the encrypted file from the writer, it executes the transaction
- A web client that provides an interface for uploading and downloading files to/from the escrow contract

![writers_market_architecture](https://user-images.githubusercontent.com/14855088/158670122-bc1b53d6-3e11-46f0-a13f-724f5c12ccb4.png)

## Logic
1. A reader (customer) funds the escrow contract with the required amount, specifying the file name they would like to buy and the writer they want to buy it from
2. The writer uploads a file to the web client, which encrypts the file with the reader's public key and sends it to the escrow contract
3. The escrow contract executes the transaction (i.e. sends the funds to the writer and the file to the reader)
4. The reader decrypts the file with their private key

## Problems
- How do readers know that the file they're receiving isn't malicious? Maybe there's a way to only allow plain text to be sent?
- Storing files in the blockchain isn't ideal, but I would set a small size limit and the file would be deleted after the transaction executes. There could also be a time limit of e.g. 24 hours, so if the transaction doesn't execute in a timely manner, the reader gets a refund.
