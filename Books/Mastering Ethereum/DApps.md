# Decentralized Applications
Smart contracts are a way to decentralize the controlling logic and payment functions of applications. Web3 DApps are about decentralizing all other aspects of an application: storage, messaging, naming, etc.

## Backend (Smart Contract)
Smart contracts store the business logic (program code) and the related state of your application. It replaces the server-side (backend) component in a regular application.

## Frontend (Web User Interface)
Interactions with Ethereum are often conducted through the web browser via a wallet extension (e.g. MetaMask).

The frontend is usually linked to Ethereum via the web3.js library.

## Data Storage
Due to high gas costs and low block gas limit, smart contracts are not well suited to storing or processing large amounts of data. Most DApps utilize off-chain data storage services, such as centralized databases or decentralized platforms (e.g. IFPS or Swarm).

### IPFS
Inter-Planetary File System is a decentralized, content-addressable storage system that distribute sstored objects among peers in a P2P network.

See https://ipfs.io

### Swarm
Swarm is another content-addressable P2P storage system similar to IFPS, developed by the Ethereum Foundation and part of Geth.

You can upload compiled frontend files to Swarm to serve the frontend directly from Swarm itself, making it truly decentralized (instead of serving from a centralized web server).

## Communication / Messaging
Inter-process communication: being able to exchange messages between applications, between different instances of an application, or between users of an application. Traditionally achieved by a centralized server, there are a variety of decentralized alternatives offering messaging over a P2P network, notably Whisper. 

## Name Resolution
Ethereum Name Service (ENS) solves the same problem as DNS (converting human-readable domain names to IP addresses) but in a decentralized manner.



