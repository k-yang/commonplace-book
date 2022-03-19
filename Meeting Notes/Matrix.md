# March 13, 2022

# March 11, 2022
Start building out the protocol with UST
How do the funding payments fix the price of the perp in our protocol?
Build out DEX, derivatives, and stablecoin as separate modules
	USDM and MTRX are the connectors
What stablecoin model do we want to use? FRAX, FEI, Kava, Dai, etc.
DEX is a mixture of Kava + Osmosis + Curve stableswaps
Derivatives is a direct copy of Perp v1
Stablecoin research TBD

## Leads Meeting
- How to integrate derivatives and DEX back into stablecoin protocol?
- Derivatives needs USDM and MTRX
- Mat wrote bot to trade derivatives on perp protocol v1
- DEX -> UST : USDM pool with MTRX rewards
- Should we create DEX on Osmosis or build our own?
	- We don't want to take on liability of Osmosis
		- There are maybe some regulatory risks of using Osmosis
		- It depends on what the value prop the DEX brings to the user. There's some legal stance we can take where we say the DEX isn't really a DEX, but just a value prop to the end user
- Derivatives create demand for USDM and value for MTRX
- DEX is Curve-style stable swap and LP tokens can be used to yield farm MTRX
- Getting to market quickly is easier if we invert the problem and frame it as "we have independent derivative and DEX protocols, how do we build a stablecoin protocol to supply that?"
- Simulation with LAs and IAs
	- It's really bad if asset collateral drops in price and stableseekers burn stablecoins to extract collateral from the protocol
- Solving the inverse problem
	- Feed a bunch of stablecoin historic price assets into DEX and derivatives protocol and see which stablecoin design works the best, and then use that design for the USDM stablecoin
	- Just implement derivatives and DEX as clones of existing protocols, and push all design complexity to the stablecoin model
	- The stablecoin model can be a clone of an existing stablecoin protocols from other ecosystems (e.g. FRAX, FEI, DAI, etc.)


# March 10, 2022
Funding payments should be scaled by LA's leverage ratio
	High leverage LAs should pay more when they're positive PnL and receive more funding payments when negative PnL
No transaction fees on entry, transaction fees on exit. Transaction fee is a percentage of your final position.
Is there an issue with different currencies on long and shorts
Funding payments can be gamed from a long position that is slightly negative in PnL
Cubic liquidation curve, long and short symmetric, together creating the IL curve that Uniswap has
Exit strategy for IF: only pay amount of margin of LAs

# March 8, 2022
Function flowchart/diagram
Bring successful projects from ETH to Cosmos
Documentation best practices
Bootstrap the module first and then it'll be easy to add features

# March 7, 2022
## Derivatives
- Vim working on perpetual bot on cosmos
- derivatives platform will work on its own as a silo
	- but will eventually complement other protocols
	- convergence is important
- Convergence
	- perpetual works with USDM
	- shouldn't be any problem if we work independently
	- stablecoin part is crucial
	- a lot of AMM work on either side
		- Kava AMM
		- Osmosis AMM
		- we are taking best features of Kava and integrating it with Osmosis
	- what flavour of perpetual
		- uniswap v3
		- perp v2
		- perp v1
		- reimplement vAMM
		- what is the motivation to implement vAMM
			- cosmos doesn't have many fees
			- vAMMs have less fees
			- vAMM is an algorithm
			- we are not inventing a new AMM algo, we are implementing the vAMM algo
- market making bot on perp protocol
- base layer on perp protocol is based on usdm (m-stables)
- Airbnb 
- orm layer for fully compatible backend