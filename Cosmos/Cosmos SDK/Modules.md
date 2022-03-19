# Modules
Modules define most of the logic of SDK applications. Developers compose modules together using the Cosmos SDK to build their custom application-specific blockchains.

SDK modules can be seen as little state-machines within the state-machine. They generally define a subset of the state using one or more `KVStore`s in the [main multistore](https://docs.cosmos.network/v0.44/core/store.html), as well as a subset of [message types](https://docs.cosmos.network/v0.44/building-modules/messages-and-queries.html#messages).

Main components of a module
- keeper, used to access and update the module's state
- msg service, used to process messages routed by BaseApp and trigger state transitions (writes, updates)
- query service, used to process user queries (reads)
- interfaces, for users to query the subset of state defined by the module and create messages defined by the module

Modules implement the `AppModule` interface in order to be managed by the [[Module Manager]].