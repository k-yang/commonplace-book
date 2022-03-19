# Module Genesis
Modules generally handle a subset of the state and, as such, they need to define the related subset of the genesis file as well as methods to initialize, verify and export it.

The subset of genesis state defined by a given module is defined in the module's `genesis.proto` file. The struct defining the module's subset of the genesis state is called `GenesisState` and contains all the module-related values that need to be initialized during genesis.

## DefaultGenesis()
Creates a simple `GenesisState` with default values for each parameter.
```go
// DefaultGenesis returns default genesis state as raw bytes for the auth
// module.
func (AppModuleBasic) DefaultGenesis(cdc codec.JSONMarshaler) json.RawMessage {
	return cdc.MustMarshalJSON(types.DefaultGenesisState())
}
```

## ValidateGenesis(GenesisState)
Verifies that a `GenesisState` is correct. It should validate every parameter in the `GenesisState`.
```go
// ValidateGenesis performs basic validation of auth genesis data returning an
// error for any failed validation criteria.
func ValidateGenesis(data GenesisState) error {
	if err := data.Params.Validate(); err != nil {
		return err
	}

	genAccs, err := UnpackAccounts(data.Accounts)
	if err != nil {
		return err
	}

	return ValidateGenAccounts(genAccs)
}
```

## InitGenesis()
Initializes the module's store's state by using a provided `GenesisState`. 
```go
// ValidateGenesis performs basic validation of auth genesis data returning an
// error for any failed validation criteria.
func ValidateGenesis(data GenesisState) error {
	if err := data.Params.Validate(); err != nil {
		return err
	}

	genAccs, err := UnpackAccounts(data.Accounts)
	if err != nil {
		return err
	}

	return ValidateGenAccounts(genAccs)
}
```

## ExportGenesis()
Exports a new `GenesisState` given the current state of the app, by reading the store via the module's keeper.
```go
func ExportGenesis(ctx sdk.Context, ak keeper.AccountKeeper) *types.GenesisState {
	params := ak.GetParams(ctx)

	var genAccounts types.GenesisAccounts
	ak.IterateAccounts(ctx, func(account types.AccountI) bool {
		genAccount := account.(types.GenesisAccount)
		genAccounts = append(genAccounts, genAccount)
		return false
	})

	return types.NewGenesisState(params, genAccounts)
}
```
