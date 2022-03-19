# Accounts
An account designates a public and private keypair.

The public key can be used to derive an address, which identify users of the application.

Addresses are associated with messages to identify the sender of the message. 

Private keys are used to generate digital signatures to prove that an address associated with a private key approved of the message. 

An HD wallet is a set of accounts derived from an initial seed secret (usually 12-24 word mnemonic). A single seed can derive any number of private keys. A public key is derived from a private key. The seed is the single most important piece of sensitive information.

# Keyring
The keyring holds private/public keypairs

The private key is stored in different locations, called "backends"

# Account Creation
An account can exist in the local keyring but not exist on the chain yet. An account is created the first time it receives tokens from another account.

```sh
$ simd keys add recipient --keyring-backend test
// the account is not created yet

$ RECIPIENT=$(simd keys show recipient -a --keyring-backend test)

$ simd tx bank send $MY_VALIDATOR_ADDRESS $RECIPIENT 1000000stake --keyring-backend test
// recipient account is created
```

You can also do `recipient --recover --keyring-backend test` if the account already exists in the keyring.

# Observations
Not all accounts need a private/public keypair. In particular, module accounts do not need a private/public keypair because they are not controlled by any human. They just need an address so that they can hold tokens.