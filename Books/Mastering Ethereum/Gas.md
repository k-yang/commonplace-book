# Gas
Gas is a resource constraining the maximum execution time of a smart contract. When the gas limit is exceeded, three things happen:
- an out of gas exception is thrown
- the state is reverted to the initial state (prior to contract execution)
- all ether used to pay for the gas is consumed (not refunded)

You can estimate gas of function calls by adding `estimateGas` after a function call. Note that it's only an estimate, but it is a good estimate most of the time.

