# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

POGPP (Proof of Global Position Protocol) is a decentralized protocol for on-chain certification of a user's geographic position, with combined validation through NFC and GPS. It integrates a Web3 infrastructure to ensure that every physical interaction is provable, traceable, and publicly verifiable.

The PAW (Proof of Activity Witnessing) technology is used as an operational framework and user portal to manage visits, authentication, and the assignment of NFT badges as proof of presence.

## Architecture

The project follows a typical web application architecture with three main components:

### Frontend (PAW Web App)
- Built with React 18, Redux Toolkit, and TailwindCSS + shadcn/ui
- Uses Web NFC API for NFC tag reading
- Uses Geolocation API for GPS coordinates
- Integrates Web3Auth for login and instant wallet creation
- Features a user interface to view visits, badges, and progress

### Backend (Express.js)
- RESTful API for validation and registration of visits
- Data storage on IPFS + versioning with IPNS
- Coordinate validation with `geolib`
- Semantic analysis of visits using `faiss-node`
- Data signing and verification for NFT issuance

### Blockchain
- `POGPPBadge.sol` contract on Gnosis Chain (ERC-721)
- NFT claim control per user and visit
- Secure minting executed only by the backend

## Visit Flow

1. User authenticates via Web3Auth (wallet creation in 1 click)
2. An NFC tag is scanned via Web NFC API
3. GPS coordinates are acquired via browser
4. Data is validated, hashed, and saved on IPFS
5. The hash is digitally signed and the CID saved on IPNS
6. If valid and not already registered, an NFT Badge is minted
7. The entire process is traceable and verifiable on-chain

## Development Commands

### Backend

```bash
# Install dependencies
cd backend
npm install

# Start development server with hot reload
npm run dev

# Start production server
npm start

# Run tests
npm test
```

### Frontend

```bash
# Install dependencies
cd frontend
npm install

# Start development server
npm start

# Build for production
npm run build

# Preview production build
npm serve

# Run tests
npm test
```

## Key Technologies

### Backend
- Node.js + Express.js
- Sequelize ORM with PostgreSQL
- IPFS via ipfs-http-client
- Vector similarity with faiss-node
- Blockchain interaction with ethers.js
- Geolocation processing with geolib
- Logging with winston

### Frontend
- React 18 with Redux Toolkit
- TailwindCSS + shadcn/ui
- Web NFC API and Geolocation API
- Web3Auth for wallet management
- Vite for build tooling

### Smart Contract
- Solidity 0.8.26
- OpenZeppelin contracts
- Deployed on Gnosis Chain

## Project Status

The project is in active development. Many files have been created but are still empty, indicating that the structure is defined but implementation is ongoing.