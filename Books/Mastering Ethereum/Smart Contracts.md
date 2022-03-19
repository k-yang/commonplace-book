# Smart Contracts
Contract accounts have associated data storage and are controlled by smart contracts

## Contract Deletion
Send SELFDESTRUCT opcode. Costs "negative gas", which is essentially a gas refund for freeing up resources in the Ethereum global state.

# Security Vulnerabilities
- minimalism/simplicity
	- the simpler the code, the easier it is to audit
- code reuse
	- use battle tested libraries and code (DRY)
- code quality
	- be rigorous
- readability/auditability
	- related to minimalism/simplicity 
	- the easier it is to read, the easier it is to spot bugs and vulnerabilities
- test coverage
	- test all inputs (even malformed or malignant ones)

## Reentrancy
When a contract sends ether to an address, that address can be a malicious contract whose fallback() function calls back into the original, vulnerable contract (code execution re-enters the original contract).

Use the transfer() function instead of send(). transfer() limits the gas in the outgoing transaction so that downstream contracts cannot re-enter the current contract.

Change state variables before ether is transferred out of the contract. This is called the checks-effects-interactions pattern.

Introduce a mutex to lock the contract so that it cannot be re-entered.

## Arithmetic Overflow / Underflow
Addition, subtraction, and multiplication can cause arithmetic operations to yield unexpected values, that can cause unexpected behaviour.

The guard is to use mathematical libraries that replace the standard addition, subtraction, and multiplication operations (e.g. SafeMath).

## Unexpected Ether
Two ways ether can be forced onto a contract (without calling any payable or fallback functions)
1. selfdestruct
	When a contract is destroyed, it sends its ether to a target address. That target address can be another contract, and when it is so, no function (even the fallback function) is called
2. pre-sent ether
	contract addresses are deterministic and can be derived from the contract creator's account address and a transaction nonce. An attacker could pre-send ether to the contract address before a contract is created, thus when the contract is created it will already have a balance

`this.balance` can be artificially manipulated by attackers and hence should not be used in any invariant checking. You can use a separate variable to keep track of deposited ether from payable functions, and that should be used in invariant checks.

## Delegate Call
Delegatecall runs another contract's function in the current context, thus using the same transaction context and storage slots. If the delegated contract updates storage slots that aren't coherent with the current contract's storage slots, things can get messed up.

Use the library keyword, which forces library contracts to be stateless and avoid the storage slot situation

## Default Visibilities
Function visibility defaults to `public`
Always explicitly set function visibility, otherwise attackers can attack functions that were meant to be private

## Entropy Illusion
All transactions on the Ethereum blockchain are deterministic state transitions, which means every transaction modifies the Ethereum global state in a predictable, deterministic way, with no uncertainty. This has the fundamental implication that there is no source of entropy or randomness in the Ethereum blockchain. 

The source of entropy or randomness must be external to the blockchain, such as commit-reveal, RandDAO, or randomness oracles. 

## External Contract Referencing
Any address can be cast to a contract, regardless of whether the code at the address represents the contract type being cast.

One mitigation is to use the new keyword to create contracts that are then referenced.

Another solution is to hardcode the external contract address.

## Short Address Parameter Attack
Parameters passed to smart contracts are encoded according to the ABI spec. Parameters shorter than the expected parameter length are suffixed with zeros. This can lead to unexpected behaviour when third party software applications do not validate input parameters before sending them in transactions.

All input parameters in external applications should be validated before sending them to the blockchain.

## Unchecked CALL Return Values
Call and Send return a boolean value indicating their success status. The transaction that executes these functions will not revert if the external call fails. A common error is that a developer expects the transaction to revert if the external call fails, and doesn't check the return value.

Use transfer over send. Transfer will revert if the external call fails. If you must use send, always check the return value.

## Race Conditions / Front Running
Users can race code execution to obtain unexpected states. Ethereum nodes pool transactions and form them into blocks. The miner who solves the block (PoW) can decide which transactions to include in the block. An attacker can watch the transaction pool for the solution to a problem and then front-run (intervene) to have their own solution included before the other transaction (e.g. by submitting the same transaction with a higher gas price).

Two classes of actors can run this attack: users who modify the gas price and miners who can reorder transactions as they see fit. 

One mitigation is to set an upper bound on the gasPrice so that attackers cannot front-run the original problem solver.

Another mitigation is to use a commit-reveal scheme. The user sends a transaction with hidden information (typically a hash). After the transaction has been committed in a block, the user sends a transaction revealing the data (reveal phase). However, this method cannot hide the transaction value. The ENS smart contract allowed users to to send transactions whose committed data included the amount of ether they were willing to spend. Then in the reveal phase, they were refunded the difference between the amount in the transaction and the amount they were willing to spend. This allows users to send transactions of arbitrary value.

## Denial of Service
Looping (too much gas)
Owner operations (owner incapacitated)
Progressing state based on external calls (these may never happen)

## Block Timestamp Manipulation
Miners can adjust block timestamp slightly, which can lead to attacks if the smart contract relies on the block's timestamp. They should not be used as the deciding factor in some state change.

It's much better to use block number, as miners cannot manipulate it as easily.

## Constructors with Care
In older versions of Solidity, the constructor was a regular function with the same name as the contract. If the contract name was changed and the developer didn't change the constructor function name, the constructor became a regular callable function which could be abused by an attacker.

In Solidity 0.4.22, the constructor keyword was introduced. 

## Uninitialized Storage Pointers
EVM stores data as either storage or memory. Local variables within functions default to storage or memory depending on their type. Local variables that default to storage can modify state variables of the contract.

This is now caught by the Solidity compiler.

## Floating Point and Precision
Solidity does not support fixed-point and floating-point numbers. Floating-point representations must be constructed with integer types in Solidity, which may lead to errors and vulnerabilities.

Keep the right decimal precision in your smart contracts. 

## Tx.Origin Authentication
Using this variable can lead to phishing attacks. Another smart contract can forward a request to the vulnerable smart contract and call authenticated functions.

## Contract Libraries
OpenZeppelin/ZeppelinOS
