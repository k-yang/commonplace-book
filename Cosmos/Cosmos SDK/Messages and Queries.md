# Messages and Queries
`Msg`s and `Queries` are the two primary objects handled by modules. Most of the core components defined in a module, like `Msg` services, `keeper`s and `Query` services, exist to process `message`s and `queries`.

Create a protobuf Msg service and register it in AppModule's RegisterServices method.