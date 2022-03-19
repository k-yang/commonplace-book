# CLI
One of the main entrypoints into the app. Allows end users to send messages (wrapped in transactions) and queries. The Cosmos SDK uses the [Cobra](https://pkg.go.dev/github.com/spf13/cobra) library for generating the CLI app.


## Transactions
Transactions trigger state changes. Transactions wrap messages. A single transaction can contain multiple messages.

Transactions typically live in `./client/cli/tx.go`.

# gRPC
RPC is the preferred way for external clients like wallets and exchanges to interact with a blockchain. The Cosmos SDK provides a gRPC proxy server that routes gRPC query requests to ABCI query requests.
```go
// RegisterGRPCGatewayRoutes registers the gRPC Gateway routes for the auth module.
func (AppModuleBasic) RegisterGRPCGatewayRoutes(clientCtx client.Context, mux *runtime.ServeMux) {
	if err := types.RegisterQueryHandlerClient(context.Background(), mux, types.NewQueryClient(clientCtx)); err != nil {
		panic(err)
	}
}
```

## REST Gateway
Applications need to support web services that use HTTP requests that don't have gRPC capabilities (e.g. Keplr wallet). grpc-gateway translates REST calls into gRPC calls. 
```protobuf
// Query defines the gRPC querier service.
service Query {
  // Accounts returns all the existing accounts
  rpc Accounts(QueryAccountsRequest) returns (QueryAccountsResponse) {
    option (google.api.http).get = "/cosmos/auth/v1beta1/accounts";
  }

  // Account returns account details based on address.
  rpc Account(QueryAccountRequest) returns (QueryAccountResponse) {
    option (google.api.http).get = "/cosmos/auth/v1beta1/accounts/{address}";
  }

  // Params queries all parameters.
  rpc Params(QueryParamsRequest) returns (QueryParamsResponse) {
    option (google.api.http).get = "/cosmos/auth/v1beta1/params";
  }
}
```

## Swagger
The SDK also provides automatic Swagger documentation.