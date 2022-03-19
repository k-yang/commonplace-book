# BaseApp
BaseApp implements the core of an SDK application, namely:
1. the ABCI
2. service routers
3. different states

Developers usually create a custom type for the app that inherits from BaseApp
```go
type App struct {
  // reference to a BaseApp
  *baseapp.BaseApp

  // list of application store keys

  // list of application keepers

  // module manager
}
```

# Service Routers
When messages and queries are received by the app, they must be routed to the appropriate module. Routing is done by `BaseApp` which holds a `msgServiceRouter` for messages and a `grpcQueryRouter` for queries.

The app's module manager registers each module's msgService by calling `RegisterServices` on every module. 

