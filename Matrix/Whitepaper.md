- USDT and USDC are centralized
- CDPs are volatile with discretionary parameters
- algorithmic stablecoins have bank run situations and liquidity crises
- volatility of collateral in reserves is hedged by perpetual futures
- Matrix will mint USDM, a stablecoin pegged to USD
- Matrix strives for over-collateralization with the use of LPs
- 

# Goal
The goal of the Matrix protocol is to mint stable assets on the Cosmos ecosystem

# Stable Users / Stable Seekers
stable users swap whitelisted collateral against stablecoins and vice versa with minimal slippage

# Liquidity Providers

## Leverage Agents
LAs get perpetual futures (leveraged positions) on a collateral/stablecoin pair
They get leveraged exposure
When LAs open a position, they bring a certain amount of collateral (margin) and choose an amount of collateral from the protocol that they want to hedge (or cover or back)

### Example
Initial price of OSMO is $10/OSMO
Protocol has 50 OSMO = $500 in collateral. Presumably $500 in stable coin is minted. c_matrix = 50 OSMO = $500.
LA puts in 10 OSMO and chooses to cover 50 OSMO. c_la = 10 OSMO = $100.
Their leverage multiplier is (c_matrix + c_la) / c_la = (50 + 10) / 10 = 6
The total collateral in the system is now 60 OSMO = $600. 
Let's say the price of OSMO moves up to $12. 
The total collateral in the system is now 60 OSMO = $720. The protocol only needs $500 to collateralize the minted stablecoin. The LA's position is the $220 surplus. The LA put in $100 and made $120, instead of just $20 had they just held the OSMO in their wallet, so the leverage is 6x (which is what we had above).
On the flip side, if the price of OSMO dropped down to $8.33~, the protocol only has 60 OSMO = $500. At this point, the LA's position gets liquidated (i.e. they don't get to keep any of what they put in). If the price moves against them by 1/6 of their position, the 6x leverage means they lose 100% of their position. That is the risk when trading with leverage. (The original 10 OSMO they put in is now worth $83.33, which is 5/6 of their original value of $100. Once it crosses this threshold, the LA loses everything).

### Equations
The total cash position of the protocol is given by price_current x (c_matrix + c_la), so the net cash position of the LA is price_current x (c_matrix + c_la) - price_initial x c_matrix = c_matrix x (price_current - price_initial) + c_la x price_current. The net cash position of the LA falls to zero when price_current = price_initial x c_matrix / (c_matrix + c_la). 



## Insurance Agents
IAs lend money to the protocol to receive transaction fees from minting/burning stablecoins and returns from lending protocol funds to other lending protocols
IAs act as a buffer when LAs do not provide enough collateral to cover the stable seekers
IAs earn interests not only on their collateral but also on the collateral of the stable seekers


# Incentive Pendulum
Matrix an incentive pendulum to get the optimal allocation of rewards between LPs and the Insurance Fund

# Insurance Fund
The insurance fund is a reserve fund to guarantee payouts to LPs.
