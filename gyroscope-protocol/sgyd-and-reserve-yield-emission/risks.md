---
description: Learn about the risks and uncertainties in GYD yield emission
---

# Risks

## Risks of Participating in Reserve Yield Emission

Since GYD is the underlying asset for the reserve yield emission processes described here, participating in it implies the same risks as using GYD (see [here](https://docs.gyro.finance/gyroscope-protocol/risks)). Furthermore, participating in the reserve yield emission system comes with certain further risks, including the following:

* Smart contract risk and upgradability risk: Reserve yield emission uses additional smart contracts in addition to the GYD system, which are subject to their own smart contract risk. As with any smart contract system, there is an inherent risk that an exploit or bug puts committed assets at risk. This risk can be reduced by conducting code audits and testing, but it cannot be fully excluded. Upgrades to the smart contracts may also introduce new bugs and vulnerabilities.
* Off-chain code execution and third-party platform risk: The off-chain program that computes yield emission may be subject to bugs that lead to an unintended emission of rewards. Third-party platforms that are used by the program may also be subject to such bugs. While this risk can be alleviated using limitations on permissions, on-chain safeguards (e.g., limits on the size of distributions, see above), and review processes, it cannot be fully excluded.
* Risks to the GYD reserve yield: The reserve yield accruing to the GYD is subject to several uncertainties, including (1) uncertainty about the yield accruing to individual reserve assets, (2) uncertainty about the value of reserve assets, (3) changes to the composition of the reserve as a result of governance changes or of actions by other actors in the ecosystem. Potential losses to reserve asset value manifest in reserve profit in an amplified way; in an extreme case, this may cause no reserve yield to be emitted across some evaluation period (emitted GYD amounts cannot be negative). While GYD is designed to limit these uncertainties, they cannot be fully excluded.

Risk of uncertain or unexpected emission of reserve yield to venues: Beyond risks to the GYD reserve and its yield themselves, there is a risk that the yield emitted to a venue may not match participants’ expectations and may in particular not be equal to the yield that the GYD reserve accrued over the same time frame (see below).

## Reserve Yield and Yield to Venues

#### Reserve Yield and Yield to Venues

The yield earned per GYD per day in the different venues need not be equal to the yield that the GYD reserve accrued across the same time frame. This is for several reasons, including the following:

1. The GYD amount emitted to venues is based on the previous period’s time-weighted GYD holdings in those venues (among other factors). Therefore, when GYD are deposited into / withdrawn from venues, this affects yield to the other holders (upwards or downwards). For pools, swaps can also change the share of the pool that is held in GYD and therefore the mathematical yield on these GYD.
2. Some uses of GYD (e.g., “raw” GYD held directly by an address) do not earn yield but the backing assets accrue yield to the reserve. Therefore, these GYD holdings can indirectly affect yield accruing to supported venues.
3. Reserve yield is not distributed equally across venues; rather, the protocol distributes yield to maximize its value and impact. Minimum and maximum weights are used for this purpose (see above). The set of supported pools may also change over time.
4. As a consequence of the emission method outlined above, uncertainty in the yield to the reserve (see above) may manifest at a different time than fluctuations to the yield to venues.
5. Also as a consequence of the emission method, yield only compounds on a per-period basis. Changes to holdings within a period do not earn compound yield.
6. Changes to the overall reserve composition and the overall reserve yield are not attributed to specific venues or specific users. For example, if a user mints new GYD using a high-yield collateral and deposits these GYD into sGYD, this does not necessarily mean that this specific user or the sGYD venue will receive higher yield.
7. The protocol may retain a portion of its yield to grow its safety buffer against future shocks.

See the README file in the [Reserve Yield Emission Scripts repository](https://github.com/gyrostable/reserve-yield-emission-scripts) for further information on potential inaccuracies of the calculation methods.
