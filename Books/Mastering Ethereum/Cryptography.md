# Public Key Cryptography
Public key is the bank account number
Private key is the PIN number
Public key is derived from private key
Private key is used to create digital signatures

# Digital Signatures
Digital signatures are created from the private key
Digital signatures are required to spend ether funds from an account or to authenticate the account to call a smart contract
Verifying a digital signature (i.e. checking that it matches the message it was attached to) means that whoever sent the message has control of the private key
Provides authentication (sender meant for the transaction to be sent), non-repudiation (the authorization cannot be denied by the sender), and message integrity (the message cannot be altered without altering the signature)

# Trapdoor Functions
Functions that are easy to calculate, but difficult to invert

# Elliptic Curve Cryptography

# Hash Functions
Creates digital fingerprints
Transforms public keys to addresses
Useful for:
- data fingerprinting
- message integrity (error detection)
- proof of work
- authentication
- pseudorandom number generation
- message commitment
- unique identifiers

Ethereum uses Keccak-256
Ethereum public addresses are the last 20 bytes of the Keccak-256 hash of the public key, which is derived from the private key using elliptic curve cryptography
