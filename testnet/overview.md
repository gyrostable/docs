---
description: Alpha testnet version of the Gyroscope Protocol
---

# Alpha version

### Conditions for minting and redeeming <a href="#conditions-for-minting-and-redeeming" id="conditions-for-minting-and-redeeming"></a>

Gyroscope checks the status of the reserve portfolio and individual assets to maintain a balanced and healthy reserve. For instance, in the Testnet Alpha, the reserve portfolio is restricted from deviating from target weights more than 10% in minting and redeeming for individual assets, and the protocol additionally checks whether individual stablecoins have depegged.

### Tracking Gyroscope Inflows and Outflows <a href="#tracking-gyroscope-inflows-and-outflows" id="tracking-gyroscope-inflows-and-outflows"></a>

Gyroscope tracks Inflow\__t and Outflow_\_t over time as exponential moving sums of inflows (minting operations) and outflows (redemption operations) with a memory half-life of 2 weeks.

### Gyroscope AMMs <a href="#gyroscope-amms" id="gyroscope-amms"></a>

The Testnet Alpha AMM calculates prices for minting and redeeming Gyro Dollars as a linear function of recent inflows and outflows and depending on the health of the reserve portfolio.

#### Minting <a href="#minting" id="minting"></a>

If the reserve capital per stablecoin is < $1, then new stablecoins can be minted for $1 worth of reserve assets. Otherwise, new stablecoins are minted for a price of1 + \epsilon \cdot Inflow\_t1+ϵ⋅Inflowt​dollar value of reserve assets, where Inflow\_t measures the rate of recent minting activity (inflows). Accounting for inflows prices the value of insurance from an over-collateralized reserve.

#### Redeeming <a href="#redeeming" id="redeeming"></a>

If the reserve capital per stablecoins is > $1, then stablecoins can be redeemed for $1 worth of reserve assets. Otherwise, stablecoins are redeemed for1 - \epsilon \cdot Outflow\_t1−ϵ⋅Outflowt​dollar value of reserve assets, where Outflow\_t measures the rate of recent redemption activity (outflows). Adjusting the redemption price to reflect recent outflows provides a variable disincentive for redemption, mitigating incentives for short-term currency crises. The parameter is tuned to change prices by $0.01 per $100k of inflows/outflows. Note that this is a simplified version of the AMM that is envisioned for later versions of the protocol. See the white paper for further details.

#### &#x20;<a href="#undefined-2" id="undefined-2"></a>

### Reserve portfolio <a href="#reserve-portfolio" id="reserve-portfolio"></a>

The reserve is a portfolio of assets that stratifies complex DeFi risks, including price risks, custodial/censorship risks, and leverage market risks. The Testnet Alpha reserve is composed of WETH, DAI, sUSD, USDC, and BUSD deployed in three Balancer pools:Balancer Pool AssetsInitial Target Portfolio WeightWETH / DAI33%WETH/ sUSD33%USDC / BUSD34%The target portfolio weights float as asset prices change (and in later implementations with governance may be periodically rebalanced). This is to protect the reserve from individual asset or pool failures, which may then only wipe out the given portion of the portfolio.The actual portfolio weights may differ from the target weights by 10% (for Testnet Alpha, may be tighter in later versions) via minting and redemption operations. In particular, stablecoins can be minted and redeemed for individual assets in the reserve up 10% portfolio deviation.\
