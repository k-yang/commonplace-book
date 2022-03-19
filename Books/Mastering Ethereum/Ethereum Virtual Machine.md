EVM executes programs and updates the state of Ethereum, constrained by consensus rules, on any node in the decentralized newtork. It is a computation engine.

In order to maintain consensus, EVM execution must be totally deterministic and based only on the shared context of the Ethereum state and signed transactions. This has two important consequences: the first is that there can be no intrinsic source of randomness for the EVM, and the second is that extrinsic data can only be introduced as the data payload of a transaction. 

The EVM has no scheduling capability because execution ordering is organized externally to it; Ethereum clients run through verified block transactions to determine which smart contracts need executing and in which order, thus the Ethereum world computer is single-threaded.

When you send a contract creation transaction to the special 0x0 address, the data field does not contain the smart contract runtime bytecode, but rather the contract's initiation (deployment) code. The EVM runs the initiation code and the output of that program is the smart contract code.

## Turing Completeness and Gas
Because it's not possible to tell whether or not a computer program will terminate (i.e. halting problem), it's possible for a smart contract to never end and DoS the Ethereum network. To solve this, Ethereum introduces the concept of gas which turns the EVM into a quasy-Turing complete machine. It can run any program, but terminates the program within a particular amount of computation.

Gas is Ethereum's unit for measuring the computation and storage resources required to perform actions on the Ethereum blockchain. 

Gas cost is the number of units of gas required to perform a particular operation.
Gas price is the amount of ether you are willing to pay per unit of gas when you send your transaction to the Ethereum network.

### Block Gas Limit
The block gas limit is the maximum amount of gas that may be consumed by all the transactions in a block, and constrains the number of transactions in a block.

