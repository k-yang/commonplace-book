Three key differentiators of the platform: engine, architectural model, governance mechanism.

# Engine
The family of consensus protocols used by Avalanche are called Snow*.
The Snow* family of consensus protocols combine the best of classic consensus protocols and Nakamoto consensus.

## Snow*
It is based on a lightweight network sampling mechanism without needing to agree on precise membership of the system
Scales to millions of direct participants without exorbitant energy expenditure of PoW

Operates by repeated sampling of network
Each node polls a small constant-sized, random set of neighbors and switches its proposal? if a majority have a different value
Samples repeat until convergence, which is fast under normal operations

# Architectural Model / Platform Overview
## Chains
### Subnets
A subnet is a dynamic set of validators working together to achieve consensus on the state of a set of blockchains
Each blockchain is validated by one subnet, and a subnet can validate an arbitrary number of blockchains
A validator may be a member of an arbitrary number of subnets

### Default Subnet
There is a special subnet called the Default Subnet validated by all validators (in order to validate in another subnet, a validator must validate for the Default Subnet). The Default Subnet validates a set of pre-defined blockchains, including the blockchain where $AVAX lives.

### Virtual Machines
Each blockchain is an instance of a VM. The interface, state, and behavior of a blockchain is defined by the VM running on the blockchain. When running a blockchain, one specifies the VM it runs as well as the genesis state.

### Bootstrapping
Process occurs in 3 stages:
1. connection to seed anchors
2. network and state discovery
3. becoming a validator

### Seed Anchors
Any networked system of peers that operates without a permissioned set of identities require some mechanism for *peer discovery*. In crypto networks, a typical mechanism is DNS seed nodes (seed anchors) from which other members of the network can be discovered.

### Network State Discovery
Once connected to a seed anchor, a node queries for the latest set of state transitions, called the *accepted frontier*. The accepted frontier is the last accepted block. The correct state is then synchronized with sampled nodes. As long as the majority of the seed anchor set are correct, then the sampled nodes must also have the accepted state transitions.

## Execution Environments

## Deployment


# Governance
