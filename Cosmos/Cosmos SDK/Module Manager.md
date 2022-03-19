# Module Manager
Cosmos SDK modules need to implement the [`AppModule` interfaces](https://docs.cosmos.network/v0.44/building-modules/module-manager.html#application-module-interfaces), in order to be managed by the application's [module manager](https://docs.cosmos.network/v0.44/building-modules/module-manager.html#module-manager). The module manager plays an important role in [`message` and `query` routing](https://docs.cosmos.network/v0.44/core/baseapp.html#routing), and allows application developers to set the order of execution of a variety of functions like [`BeginBlocker` and `EndBlocker`](https://docs.cosmos.network/v0.44/basics/app-anatomy.html#begingblocker-and-endblocker).

The module manager plays an important role in message and query routing.

The application module interface is implemented in a `./x/module/module.go`. Every module needs to implement the `AppModuleBasic` and `AppModule` interfaces. 

Module managers are used to manage collections of `AppModuleBasic` and `AppModule`. It also sets the order dependency between modules.