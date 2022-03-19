# Whitepaper
Cryptocurrencies (e.g. Bitcoin) are governed by simple and deterministic growth. As a result, unanticipated changes in coin demand are reflected in the coin price, causing volatility and discouraging use of the coin. 

Next generation cryptocurrencies should incorporate an elastic supply rule that adjust the quantity of coin supply in proportion to market value. 

"The main volatility in bitcoin comes from variability in speculation, which in turn is due to the genuine uncertainty about its future." - Nick Szabo

Deterministic coin supply is a bug rather than a feature.

## Coin Demand
Two types of coin demand:
1. Transactional Coin Demand
   Amount of coins held for making transactions
2. Speculative Coin Demand
   Amount of coins held with the expectation that the coin price will increase
$$
CD = CD_T + CD_S
$$
Coin demand is a function of purchasing power rather than quantity of a coin.
$$
CD = P x Q
$$

## Elastic Coin Supply
Changes in coin demand equate to changes in coin price. In a stabilization scheme, the coin price will change in response to a change in coin price. When there is an X% change in coin price, the coin supply will also change by X% to stabilize the price. 

The rebase period is the interval of time used to calculate the X% change in price, defined as *n* blocks. 

There are two hard problems to solve
1. How can the price be represented in the network in a trustworthy way?
   Oracles?
2. How can the change in supply be fairly distributed?
   

## Change in Supply
In a stabilization scheme, even if the expected coin supply increase is positive, there are times when the coin supply decreases, and coin stabilization needs a mechanism for reducing the coin supply as well as increasing it, so the mining award channel isn’t a solution to the problem of how the change in coin supply is distributed.