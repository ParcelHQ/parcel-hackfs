# Parcel HackFS submission


Parcel is a decentralized crypto payroll service with built-in end-to-end data encryption using Filecoin, IPFS, Textile’s Powergate and Sablier for money streaming.

# How do i setup ? 
```
git clone https://github.com/ParcelHQ/parcel-ui
cd parcel-ui
npm install
npm start
```

# Description
This project enable organisations to run crypto payroll seamlessly using mass payouts for multiple tokens and money streaming in one single transaction with the help of transactions batching.

It also ensures end to end encryption for organisation data on IPFS and Filecoin and the encryption key is calculated deterministically though signatures using ethereum private key.

Moreover, Parcel is built to empower people to receive payments in real time and employers to run payroll and manage organisation documents without any hassle.

## Components 
1. Parcel Contracts :- It contains the smart contracts code for creating organisation using ENS names, running mass payouts and money streaming using Sablier protocol and Swap tokens using Uniswap. The idea of mass payouts is inspired from the initial version of Parcel which was built at Hack Money Hackathon. However, the code for the mass payouts in this version is different from what is being used in initial version. Repo Link :- https://github.com/ParcelHQ/parcel-contracts 
, Hack Money Project Link :- https://hack.ethglobal.co/showcase/parcel-recUVCg0viNysWQAs 

2. Parcel UI : It contains the code for user interface for the application built with Reactjs. 
Repo Link : https://github.com/ParcelHQ/parcel-ui

3. Parcel SDK : It includes all the methods to interact with IPFS gateway via end to end encryption and this component is being used on the client side with Parcel UI. Repo Link : https://github.com/ParcelHQ/parcel-sdk 

4. Parcel Filecoin Archiving: It includes the code for getting the ipfs hashes from smart contracts and fetch the data from IPFS and archive it on Filecoin using Textile's Powergate. The main purpose of this component is to make sure data is persisted on Filecoin. In case of unavailability of data on IPFS, it can retrieve the data from filecoin and push it back to IPFS . Repo Link : https://github.com/ParcelHQ/parcel-filecoin-archiving

# How It's Made

## Technology Stack includes
1. Sablier Protocol for money streaming.
2. Uniswap for token swapping
3. IPFS for encrypted data storage. 
4. Fleek for website hosting. 
5. Textile's Powegate for encrypted data archiving on Filecoin.
6. Ethereum signature for generating encryption keys deterministically.
7. Metamask for wallet management.

Let's understand the workflow for adding, getting and updating user's data and documents on IPFS and Smart contracts.

## Adding Data:- 
1. Generate encryption keys by signing a deterministic string using Ethereum private keys and then hash it with the hashing algorithm. 
2. Encrypt data with the generated key. 
3. Calculate the master hash from IPFS for the particular section e.g "Documents" in an organisation and attach encrypted data to this master hash and then store it in a smart contract by doing a transaction and map it to index. 

## Getting data:
1. Generate encryption keys by signing a deterministic string using Ethereum private keys and then hash it with the hashing algorithm. 
2. Fetch the IPFS hashes from the smart contract. 
3. Get the encrypted data from the IPFS. 
4. Decryption the data locally with the generated key. 

## Updating data:
1. Generate encryption keys by signing a deterministic string using Ethereum private keys and then hash it with the hashing algorithm. 
2. Fetch the IPFS hashes from the smart contract. 
3. Get the encrypted data from the IPFS. 
4. Decryption the data locally with the generated key. 
5. Encrypt the updated data with the generated key. 
6. Calculate the master hash for the updated encrypted data from IPFS and then store it in a smart contract by doing a transaction and map it to same index. 

