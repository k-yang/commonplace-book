# Pricefeed Module
`x/pricefeed` is an implementation of a Cosmos SDK Module that handles the posting of prices for various markets by a group of whitelisted oracles. At the end of each block, the median price of all oracle posted prices is determined for each market and stored. [Spec](https://github.com/Kava-Labs/kava/tree/master/x/pricefeed/spec)

## How does price get updated?
Oracles run as daemons on blockchain nodes and send price update transactions to the blockchain. See [docs](https://docs.kava.io/tools/oracle.html) for more information. 

## How do oracles get configured?
The list of accepted oracles is provided via the genesis file at blockchain creation time. The genesis file has a list of markets (token-pairs) and accepted oracles for each market. See [GitHub](https://github.com/Kava-Labs/kava/blob/master/proto/kava/pricefeed/v1beta1/genesis.proto) for the genesis state subset belonging to the pricefeed module.