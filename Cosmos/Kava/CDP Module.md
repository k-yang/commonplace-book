# CDP Module
A CDP enables the creation of a stable asset pegged to an external price (usually US Dollar) by collateralization with another asset. Collateral is locked in a CDP and new stable asset can be minted up to some fraction of the value of the collateral. To unlock the collateral, the debt must be repaid by returning some stable asset to the CDP at which point it will be burned and the collateral unlocked.

Pegged assets remain fully collateralized by the value locked in CDPs. In the event of price changes, this collateral can be seized and sold off in auctions by the system to reclaim and reduce the supply of stable assets. 

[Spec](https://github.com/Kava-Labs/kava/tree/master/x/cdp/spec)

cdp module uses the pricefeed, auth, and bank modules [GitHub](https://github.com/Kava-Labs/kava/blob/ffef832d454656ab769ed83a6a3ea2ec514f3666/x/cdp/module.go#L100-L119).

---
## Proto Transactions
- CreateCDP
- Deposit
- Withdraw
- DrawDebt
- RepayDebt
- Liquidate

## Proto Queries
- Params
- Accounts
- TotalPrincipal
- TotalCollateral
- Cdps
- Cdp
- Deposits

## Proto State
```protobuf
// CDP defines the state of a single collateralized debt position.  
message CDP {  
  uint64 id    = 1 [(gogoproto.customname) = "ID"];  
 bytes owner = 2 [  
    (cosmos_proto.scalar) = "cosmos.AddressBytes",  
 (gogoproto.casttype)  = "github.com/cosmos/cosmos-sdk/types.AccAddress"  
 ];  
 string type             = 3;  
 cosmos.base.v1beta1.Coin  collateral       = 4 [(gogoproto.nullable) = false];  
 cosmos.base.v1beta1.Coin  principal        = 5 [(gogoproto.nullable) = false];  
 cosmos.base.v1beta1.Coin  accumulated_fees = 6 [(gogoproto.nullable) = false];  
 google.protobuf.Timestamp fees_updated     = 7 [(gogoproto.stdtime) = true, (gogoproto.nullable) = false];  
 string interest_factor  = 8 [  
    (cosmos_proto.scalar)  = "cosmos.Dec",  
 (gogoproto.customtype) = "github.com/cosmos/cosmos-sdk/types.Dec",  
 (gogoproto.nullable)   = false  
 ];  
}

// Deposit defines an amount of coins deposited by an account to a cdp  
message Deposit {  
  uint64 cdp_id    = 1 [(gogoproto.customname) = "CdpID"];  
 string depositor = 2 [  
    (cosmos_proto.scalar) = "cosmos.AddressBytes",  
 (gogoproto.casttype)  = "github.com/cosmos/cosmos-sdk/types.AccAddress"  
 ];  
 cosmos.base.v1beta1.Coin amount = 3 [(gogoproto.nullable) = false];  
}
```


## Module Flow
1. Obtain latest price from pricefeeds
2. Update interest owed to total debt
3. Updates the stability fees owed for individual CDPs
4. Liquidate any CDPs that are below the collateral-principal liquidation ratio
5. Run the debt and surplus auction

## Liquidation
1. The current price of the collateral is fetched from the pricekeeper module
2. The liquidation ratio is read from the module params
3. All CDPs below the liquidation ratio are fetched
4. Collateral is seized for every CDP below the liquidation ratio

## Seizing Collateral
1. Collateral is sent from module account to liquidator account
2. CDP is closed
3. Collateral is auctioned off from liquidator account
https://github.com/Kava-Labs/kava/blob/c2257c409659e2a6c1c8907fe5ae596c5e46f19d/x/cdp/keeper/seize.go#L34-L112