# CDP Concepts
A CDP only has one collateral type.
It has one owner, and a set of depositors. The owner can deposit and withdraw stable assets and collateral. Depositors can deposit and withdraw collateral to the CDP. 

## User Interactions
-   create a new CDP by depositing a supported coin as collateral and minting debt
-   deposit to a CDP controlled by a different owner address
-   withdraw deposited collateral, if it doesn't put the CDP below the liquidation ratio
-   issue stable coins from this CDP (up to a fraction of the value of the collateral)
-   repay debt by paying back stable coins (including paying any fees accrued)
-   remove collateral and close CDP

## Module Interactions
-   fees for all CDPs are updated each block
-   the value of fees (surplus) is divded between users, via the savings rate, and owners of the governance token, via burning governance tokens proportional to surplus
-   the value of an asset that is supported for CDPs is determined by querying an external pricefeed
-   if the price of an asset puts a CDP below the liquidation ratio, the CDP is liquidated
-   liquidated collateral is divided into lots and sent to an external auction module
-   collateral that is returned from the auction module is returned to the account that deposited that collateral
-   if auctions do not recover the desired amount of debt, debt auctions are triggered after a certain threshold of global debt is reached
-   surplus auctions are triggered after a certain threshold of surplus is triggered

---
# Fees
A user pays a fee when they repay a stable asset withdrawn from a CDP. It depends on the amount of stable asset withdrawn and the time withdrawn for.

A further fee is applied on liquidation of a CDP. 

The `feeRate` is a per second debt interest rate.
Fees are divided between surplus and savings rate. 

The fees go to the liquidation module as surplus.

The incentive module takes care of paying out the USDX holders.

---
# Liquidation
The ratio of collateral value to debt value in each CDP is monitored. When this drops below the liquidation ratio the collateral and debt is automatically seized and auctioned off.

---
# Debt
## Debt Auction
If the liquidation fails to cover the debt, deb auctions occur. A debt auction is where system governance tokens are minted and sold through auction to raise enough stable assets to cover the remaining debt.

## Debt Tracking
Users incur debt when they draw new stable assets from their CDP. The system tracks this debt as "debt coins" stored internally in the module's accounts. A stable coin corresponds to a debt coin and debt coins are burned when stable coins are returned.

The cdp module has two accounts:
- one to hold debt coins associated with active CDPs
- liquidator account to hold seized debt from CDPs
## DebtDenom
The name of the internal debt coin
## TotalPrincipal
Sum of all non-seized debt plus accumulated fees

---
# Surplus
Surplus fees are auctioned off for governance tokens. The governance tokens are burned, thereby deflating the governance token.

---
# CDP
A CDP is a struct representing a debt position owned by one address. It has one collateral type and records the debt that has been drawn and how much fees should be repaid. Only an owner is authorized to draw or repay debt, but anyone can deposit collateral to a CDP.

---
# Deposits
Deposits are scoped per address and are recorded separately in a `Deposit` struct.

---
# Savings Rate
They took it out in [this PR](https://github.com/Kava-Labs/kava/pull/764/files) and replaced it with the incentive module.

---
# Update Fees
Why are debt coins minted and sent to the CDP's module account?
- Keeps track of how much the user owes
Why are stable coins minted and sent to the system's liquidator module account?
- The stability fees are recuperated as surplus and auctioned off for governance tokens, which are then burned.
