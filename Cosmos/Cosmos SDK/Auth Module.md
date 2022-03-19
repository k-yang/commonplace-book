# Auth Module
[Docs](https://docs.cosmos.network/v0.44/modules/auth/)
Responsible for specifying the base transaction and account types for an application --> fundamental module

## Accounts
Accounts contain authentication information for a uniquely identified external user of an SDK blockchain, including public key, address, and account number / sequence number for replay protection. For efficiency, since account balances must also be fetched to pay fees, account structs also store the balance of a user as `sdk.Coins`.

## Keeper
One fully-permissioned account keeper is exposed