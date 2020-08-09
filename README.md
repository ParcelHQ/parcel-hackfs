# Parcel HackFS Submission

Parcel is a decentralized, crypto payroll service with built-in end-to-end data encryption using Sablier, Filecoin, IPFS, & Textile’s Powergate.

## Setup

```bash
git clone https://github.com/ParcelHQ/parcel-ui
cd parcel-ui
npm install
npm start
```

## [HackFS Showcase](https://hack.ethglobal.co/showcase/parcel-recMzBP7HUVYDYQIR)

## Description

Parcel enables organizations to seamlessly run crypto payroll (with multiple tokens) through mass payouts and/or money streaming in one single transaction (via transaction batching). It ensures end-to-end encryption for organization data on IPFS and Filecoin and the encryption key is calculated deterministically through signatures using an Ethereum private key. Moreover, Parcel is built to empower people to receive payments in real-time and employers to run payroll and manage organization documents without any hassle.

### Components

1. **[Parcel Contracts](https://github.com/ParcelHQ/parcel-contracts/tree/massPayouts)**: Contains the smart contracts for creating an organization using ENS names, running mass payouts, and money streaming using Sablier protocol and Swap tokens using Uniswap. The idea of mass payouts is inspired by the initial version of Parcel which was built at [ETHGlobal's Hack Money Hackathon](https://hack.ethglobal.co/showcase/parcel-recUVCg0viNysWQAs). However, the code for the mass payouts in this version is different from what is being used in the initial version.

2. **[Parcel UI](https://github.com/ParcelHQ/parcel-ui)**: Contains the UI for the application. Built with Reactjs, Ether.js, Emotion, & Reactstrap.

3. **[Parcel SDK](https://github.com/ParcelHQ/parcel-sdk)**: Includes all the methods to interact with IPFS gateway via end to end encryption and this component is being used on the client-side with Parcel UI.

4. [Parcel Filecoin Archiving](https://github.com/ParcelHQ/parcel-filecoin-archiving): It includes the code for getting the IPFS hashes from smart contracts and fetch the data from IPFS and archive it on Filecoin using Textile's Powergate. The main purpose of this component is to make sure data is persisted on Filecoin. In case the data is unavailable on IPFS, it can retrieve the data from Filecoin and push it back to IPFS.

## How It's Made

### Tech Stack

1. Sablier Protocol for money streaming.
2. Uniswap for token swapping
3. IPFS for encrypted data storage.
4. Fleek for website hosting.
5. Textile's Powegate for encrypted data archiving on Filecoin.
6. Ethereum signature for generating encryption keys deterministically.
7. Metamask for wallet management.

Let's understand the workflow for adding, getting and updating a user's data and documents.

### Adding Data

1. Generate encryption keys by signing a deterministic string using Ethereum private keys and then hash it with the hashing algorithm.
2. Encrypt data with the generated key.
3. Calculate the master hash from IPFS for the particular section e.g "Documents" in an organization and attach encrypted data to this master hash and then store it in a smart contract by doing a transaction and map it to index.

### Getting data

1. Generate encryption keys by signing a deterministic string using Ethereum private keys and then hash it with the hashing algorithm.
2. Fetch the IPFS hashes from the smart contract.
3. Get the encrypted data from the IPFS.
4. Decrypt the data locally with the generated key.

### Updating data

1. Generate encryption keys by signing a deterministic string using Ethereum private keys and then hash it with the hashing algorithm.
2. Fetch the IPFS hashes from the smart contract.
3. Get the encrypted data from the IPFS.
4. Decrypt the data locally with the generated key.
5. Encrypt the updated data with the generated key.
6. Calculate the master hash for the updated encrypted data from IPFS and then store it in a smart contract by creating a transaction and mapping it to the same index.
