https://docs.soliditylang.org/en/v0.8.12/installing-solidity.html

# Application Binary Interface
ABI is the interface between the OS and user program (machine code)
It is a JSON array of function and event descriptions
Any application can interact with the smart contract by looking at it's ABI (in JSON representation)

# Functions
The smart contract function without a name is called the fallback function, and it cannot have any arguments or return anything

## view
view functions promise not to modify the state
## pure
pure functions do not read or write any data from/to storage. They encourage declarative-style programming.
## payable
payable functions can receive incoming payments
## constructor
optional function that is run at contract creation time, to initialize state

## SELFDESTRUCT
Contracts are destroyed by the EVM bytecode SELFDESTRUCT

You must explicitly add a function that calls selfdestruct(address) in order for it to be deletable

# Function Modifier
Modifiers are conditions that are applied to many functions. You apply modifiers by adding the function modifier name to the function declaration. An example would be a modifier that only allows the owner to call the function.

Most often used for access control

# Inheritance
Solidity supports contract inheritance. It also supports multiple contract inheritance

# Error Handling
Handled by functions assert, require, revert, throw (deprecated)
When a contract terminates with an error, all state changes (all the way up the chain of contract calls) is reverted, making transactions atomic. Either a transaction changes the global Ethereum state, or it doesn't.

By convention, assert is used to test internal conditions and require is used to test inputs

# Events
When a transaction completes, it produces a transaction receipt, which contains log entries that contain information about the actions that occurred during the transaction execution. Events are the Solidity high-level objects that are used to construct these log entities.

# Calling Other Contracts
Inherent risks come from not knowing which contracts are calling into your contract or the details of the contract you are calling

You can create new contracts from within smart contract code

You can also cast an address to a contract that you already know. It's vital to know that the instance you are casting is the correct type.

You can also raw call another contract by using it's address, function name, and arguments. It opens up the security risk of reentrancy.

delegatecall is like call, but it doesn't change the message context (e.g. msg.sender is the same as the calling contract's context). It's useful with library functions.

When you call a library function, it inherits the execution context of the caller. When you call a contract function, it has it's own context. When you delegate call a contract function, it inherits the execution context of the caller.



# Dangers (addressed by Vyper)
function modifiers altering internal contract state
function modifiers are pervasive and if they are re-used by developers without proper checking, they can lead to unintended side effects

multiple inheritance requires jumping through multiple files, which can obscure behaviour and lead to mistakes

inline assembly is dangerous

function overloading is confusing

explicit typecasting > implicit typecasting

