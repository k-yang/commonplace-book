Binary wire encoding of types in Cosmos can be broken down into two categories:
1. client encoding
   - transaction processing and signing
2. store encoding
   - state machine transitions
   - stored in Merkle tree

Encoding is important because it reduces the size of payloads and storage and makes the system overall more efficient and scalable.

Cosmos SDK used to use [Amino](https://github.com/tendermint/go-amino/) encoding, but is going to start using [gogoprotobuf](https://github.com/gogo/protobuf/) for encoding. 