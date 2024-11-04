# Ethereum DID Registry Contract

This library is an implementation of a registry contract that supports the Ethereum DID Method.

## Overview

The Ethereum registry contract acts as a public ledger, where the Ethereum-Identity specified Decentralised Identifiers will be logged. The specifications related to ethereum DID method are mentioned in the document. A DID generated using the Ethereum DID generator, can be stored and managed on the ledger using this contract library.

## Contract Deployment

|        Network         | ChainId |              Registry Address              |
| :--------------------: | :-----: | :----------------------------------------: |
|    Ethereum Mainnet     |   1   |  |
| Ethereum Testnet (Sepolia) |  11155111  | 0xF81c20E4faf223b77A9eb2610113cb07f9f320b0 |

## Methods

- `createDID(address, string)` : The method createDID is used to create and log a new DID on the ethereum chain. The parameter of address type, will act as the reference key, to refer the did document stored on the chain. The string type variable will contain the did document, that will be stored on the ethereum chain.

- `updateDIDDoc(address, string)` : The method updateDID is included in contract, which will facilitate the controller, and only the controller of the did, to update the document if need arises. Though the Ethereum DID method, defines how the DID doc is defined as per standards, and that can be resolved.

- `getDIDDoc(address)` : The method getDID helps to resolve the DID document.

- `transferOwnership(address)` : The method transferOwnership, helps in transferring the ownership of contract to a new owner. Only the current owner can access this function.

- `getOwner()` : the method getOwner helps one to fetch the current owner of the contract.

- `addResource(address, string, string)` : The addResource method allows the controller of a DID to add a linked resource to the DID document. This method ensures that only authorized controllers can add resources by requiring the caller to be the controller of the DID.

- `getResource(address, string)` : The getResource method fetches a specific linked resource from the blockchain that is associated with a given DID document.

- `getAllResources(address)` : The getAllResources method retrieves all resources linked to a specific DID document. This provides a comprehensive list of all resources associated with a given DID.

## Example ethers code

Using ethers, the following illustrates how one can interact with EthereumRegistry contract, from client side application.

## Loading the Contract

```
const ethers = require('ethers');
const url = https://rpc2.sepolia.org; // For amoy testnet
const DID_ADDRESS = `<Contract Address>`;
const provider = new ethers.providers.JsonRpcProvider(url);

let wallet = new ethers.Wallet(`<Signer Key/Private Key>`, provider);
let registry = new ethers.Contract(DID_ADDRESS, <Contract ABI>, wallet);
```

# Deploying the Contract on Ethereum network

Pre-requisites

- NodeJS - https://nodejs.org/en/download/
- Hardhat - https://hardhat.org
- A wallet connected to ethereum network, with ethers in it. One can receive the Sepolia Test Tokens from their faucet.

## Deployment

Clone the repository

```
git clone https://github.com/cedoor/ethereum-did-registry-contract
```

Install Dependencies

```
pnpm i
```

Update your and RPC URL in .env file.

```
SIGNER="<Place your Signer Key here>"
```

On a new console window run

```
npx hardhat run deploy --network <network name>
```

## Testing

For Testing use the command

```
pnpm test
```
