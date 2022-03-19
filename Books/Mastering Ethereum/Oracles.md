# Oracles
Systems that can provide external data sources to smart contracts. Oracles bridge the gap between the off-chain world and smart contacts. 

Oracles collect data from an off-chain source, transfer the data on-chain with a signed message, and then make the data available by putting it in a smart contract's storage.

Three main ways:
1. request-response
2. publish-subscribe
3. immediate-read

## Immediate-Read
Provide data that is only needed for an immediate decision. The lookup is done when the information is needed and possibly never again.

## Publish-Subscribe
Oracle provides a broadcast service for data that is expected to change. Smart contract is either polled by another on-chain smart contract, or an off-chain daemon. 

## Request-Response
Used where data space is too large to be stored in a smart contract and users only need a subset of data at a time. Smart contract calls oracle contract which initiates an off-chain data request. The off-chain infrastructure sends back the response to the requesting smart contract via arguments retrieved from the request. 

# Data Authentication
## Authenticity Proofs

## Trusted Execution Environments

# Computation Oracles
Offload expensive computations off-chain via computation oracles.
# Decentralized Oracles
Centralized or computation oracles represent a single point of failure in the Ethereum network. 
[[Chainlink]] proposes a decentralized oracle network consisting of three key smart contracts:
1. a reputation contract
2. an order-matching contract
3. an aggregation contract
And a registry of off-chain data providers.

