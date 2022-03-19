# Cosmos
Cosmos is a network of interoperable blockchains. It is an ecosystem of wallets, services, tokens, and dApps.

## Blockchains
Blockchain protocols define programs that hold a state and describe how to modify the state according to the received inputs. The inputs are called transactions.

The consensus mechanism ensures that a blockchain has a canonical transaction history. A blockchain architecture can be split into three layers:
1. The network layer: tasked with node discovery and transaction propagation between nodes
2. The consensus layer: runs the consensus protocol between nodes
3. The application layer: runs the state machine that defines the application state and updates it with processing transactions abiding with the consensus rules

The Ethereum application layer is the EVM. The EVM runs smart contracts, providing a single chain on which to deploy programs. Despite its benefits, the EVM is a sandbox that allows for simplistic and minor complex use cases, but is limited regarding design and efficiency. 

Some general issues of a public general-purpose blockchain:
- low flexibility for developers
- difficulties with speed
	- speed means transaction speed
- throughput
	- how many transactions the network can handle per unit of time
	- impacts scalability of dApps
- scalability
- state finality
	- finality describes whether and when committed blocks can no longer be reverted or revoked
	- there is probabilistic and absolute finality
		- probabilistic describes the finality of a transaction dependent on how probable reverting a block is
			- PoW + longest chain rule results in probabilistic finality
		- absolute finality means that no block can be reverted
			- trait of PoS protocols
- sovereignty
	- In traditional general-purpose blockchains, applications all share the same underlying environment. Application changes depend on the governance of the application and also the underlying chains' governance. The chain's governance limits the application's sovereignty, called two-layer governance.
	- Cosmos allows developers to build application-specific blockchains tailed to the application, so there is no limit to the application's sovereignty. This is called one-layer governance.


# Consensus Algorithm
[Tendermint Consensus](https://docs.tendermint.com/master/introduction/what-is-tendermint.html)

# State Machines
A blockchain is a replicated state machine at its core. A state transition function in a blockchain is synonymous with a transaction. Given an initial state, a confirmed transaction, and a set of rules for interpreting that transaction the machine transitions to a new state. The rules of interpretation are defined at the application layer.

# Bonding
Process of locking up staking tokens for a period of time to obtain voting power. Bonded tokens give the right to rewards and are exposed to slashing.