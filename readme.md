# HTML-TS-FundMe

![TypeScript](https://img.shields.io/badge/TypeScript-Strict-blue)
![viem](https://img.shields.io/badge/viem-1.x-purple)
![MetaMask](https://img.shields.io/badge/MetaMask-supported-orange)
![Network](https://img.shields.io/badge/network-localhost%20%7C%20testnet-lightgrey)

## About

HTML-TS-FundMe is a minimal, framework-free TypeScript Web3 frontend built with viem that interacts with a payable FundMe smart contract via MetaMask.

The project intentionally avoids frontend frameworks to focus on correct protocol interaction patterns, strict TypeScript typing, and clean separation between read and write operations. It mirrors real-world dApp logic rather than UI abstraction.

This repository is intended as both a learning exercise and a portfolio artifact.

## Features

- MetaMask wallet connection
- Chain-aware wallet and public clients
- Fund a payable fund() function with ETH
- Withdraw all contract funds via withdraw() (owner-only)
- Read on-chain ETH balance of the contract
- Transaction simulation before execution
- Waits for transaction confirmation before state reads
- Strict TypeScript with viem 1.x
- Pure HTML + TypeScript (no frameworks)

## Quickstart

Requirements:
- Node.js >= 18
- MetaMask browser extension
- Local Ethereum node (Anvil / Hardhat) or testnet RPC

Installation:
- git clone https://github.com/Alpy16/HTML-TS-Fundme.sol.git
- cd HTML-TS-Fundme.sol
- npm install

Environment setup:
- constants-ts.ts must export a typed contract address and ABI
- RPC URL defaults to http://localhost:8545 and can be changed in index-ts.ts

## Usage

Connect Wallet:
- Click Connect
- MetaMask prompts for account access
- Wallet client is initialized for the active chain

Fund Contract:
- Enter an ETH amount
- Click Fund
- Flow: simulate -> send transaction -> wait for confirmation -> refresh balance

Get Balance:
- Click Get Balance
- Reads the contract’s ETH balance directly from the chain

Withdraw:
- Click Withdraw
- Calls the owner-only withdraw() function
- Waits for confirmation and refreshes balance

## Project Structure

.
├── index.html          Minimal UI  
├── index-ts.ts         TypeScript logic (viem + MetaMask)  
├── constants-ts.ts     Contract ABI and address  
├── package.json  
├── tsconfig.json  
└── README.md  

## Design Notes

- Uses viem instead of ethers.js for explicit, type-safe interactions
- walletClient is used only for signing and sending transactions
- publicClient is used for reads, simulations, and receipts
- Avoids race conditions by waiting for transaction finality
- Written to reflect real protocol frontend architecture

This codebase can be extended into an event-driven dashboard, backend service, or admin panel.

## License

MIT
