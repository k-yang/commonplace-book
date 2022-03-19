# Transactions
Only things that can trigger a change of state, or cause a contract execution

## Fields
- nonce
	-  A scalar value equal to the number of transactions sent from this address or, in the case of accounts with associated code, the number of contract-creations made by this account.
	-  controls ordering of multiple transactions sent from a single account
	-  protects against replay attacks
- gas price
- gas limit
- recipient
- value
- data
- v,r,s ecdsa signature

## Gas
Gas is the fuel of Ethereum. It is not ether, but is it's own virtual currency that has an exchange rate against ether.

## Ether Burn
Ether sent to 0x0 or the special burn address is lost forever (called an intentional burn)

## Contract Creation
Transactions sent to 0x0 are meant to create contracts. The transaction contains a data payload that is the compiled bytecode of the smart contract
