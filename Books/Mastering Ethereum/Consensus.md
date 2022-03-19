# Consensus
In the context of blockchains, consensus is the mechanism at which decentralized nodes are able to arrive at a common state, while maintaining decentralization. Consensus is intended to produce a system of strict rules without rulers. 

A consensus mechanism is the combination of Sybil resistance and a chain selection rule. Sybil resistance is the ability to resist Sybil attacks and chain selection is to decide which chain is the correct chain.

Nakomoto consensus is PoW Sybil resistance + longest chain rule. 

## Proof of Work (PoW)
PoW is the most important invention underpinning Bitcoin. The colloquial term for PoW is mining. The real purpose of mining (and all other consensus models) is to secure the blockchain while keeping control over the system decentralized and diffused across as many participants as possible. 

## Proof of Stake (PoS)
The blockchain keeps track of a set of validators, and anyone who holds the blockchain’s base cryptocurrency (in Ethereum’s case, ether) can become a validator by sending a special type of transaction that locks up their ether into a deposit. The validators take turns proposing and voting on the next valid block, and the weight of each validator’s vote depends on the size of its deposit (i.e., stake). Importantly, a validator risks losing their deposit if the block they staked it on is rejected by the majority of validators. Conversely, validators earn a small reward, proportional to their deposited stake, for every block that is accepted by the majority. Thus, PoS forces validators to act honestly and follow the consensus rules, by a system of reward and punishment. The major difference between PoS and PoW is that the punishment in PoS is intrinsic to the blockchain (e.g., loss of staked ether), whereas in PoW the punishment is extrinsic (e.g., loss of funds spent on electricity).


https://www.youtube.com/watch?v=dylgwcPH4EA

