---
description: Elliptic Liquidity Pools or E-CLPs for asymmetric concentrated liquidity
---

# E-CLPs

## Description of E-CLPs

**Elliptic CLPs, or E-CLPs, allow trading along the curve of an ellipse. E-CLPs will be used for stablecoin pools that include the Gyroscope stablecoin, GYD.**

Elliptic CLPs, or E-CLPs, allow trading along the curve of an ellipse. Similar to other CLPs, E-CLPs are designed to concentrate liquidity within price bounds. The difference is that E-CLP liquidity is more flexible: it can be further focused asymmetrically and not spread uniformly across the price range.

E-CLPs will be used for GYD trading markets, which are pools that pair GYD against other assets, and are calibrated to provide liquidity primarily around the peg, but with price bounds tailored to DSM redemption prices.

{% hint style="info" %}
By performing different manipulations on a circle, the E-CLP can be calibrated to different use-cases. The main use-cases are listed below with colloquial explanations:

* Symmetric stretch: price-bounded ‘StableSwap’ \[1]&#x20;
* Asymmetric stretch: high liquidity at 1$, with residual liquidity at other prices&#x20;
* Constant circle: alternative to constant product concentrated liquidity
{% endhint %}

The below visual representation shows how the E-CLP can be calibrated to have price-bounds, an upper ceiling of 1 USD, and an unevenly decaying price below 1 USD.

<figure><img src="../../.gitbook/assets/E-CLP-v1 (2) (1).gif" alt="Stylized visualztion of an E-CLP with price-bounds, an upper ceiling of 1 USD, and an unevenly decaying price below 1 USD.Reduc"><figcaption><p>Stylized visualztion of an E-CLP with price-bounds, an upper ceiling of 1 USD, and an unevenly decaying price below 1 USD.</p></figcaption></figure>

E-CLPs are simple and efficient. By putting liquidity only where it is needed, E-CLPs can improve capital efficiency by upwards of 75% over StableSwap pools.

<figure><img src="../../.gitbook/assets/E-CLP-liquidity-density-animated-chart-v6.gif" alt=""><figcaption><p>The E-CLP's asymmetric concentrated liquidity improves capital efficiency over StableSwap by putting liquidity only where it is needed.</p></figcaption></figure>

## Benefits of E-CLPs

E-CLPs have two main properties, price bounds and an uneven liquidity profile between the price bounds. These properties allow pools with highly customizable liquidity profiles, which can greatly increase capital efficiency in the most commonly expected trading ranges.

**Customizable liquidity profiles**: Using the curve of an ellipse allows highly customizable and _asymmetric_ liquidity profiles. E-CLPs can be calibrated to approximate most trading curves that would be desired. E-CLP curves can be tailored to have certain regions of low price impact and other regions of high price impact.

For instance, E-CLPs can be made to resemble the liquidity profiles of Stableswap curves as well as constant product curves and a flexible combination of these.

**Price bounds**: The E-CLP's price-bounds enable the E-CLP to be highly capital-efficient. Functionally, this works by enabling arbitrary truncation of liquidity profiles from a given trading curve. In effect, the capital efficiency comes from bounding the trading curve to an expected trading range of the assets.

In settings where the structure of assets leads to knowledge of trading price constraints or market makers otherwise know that it is unprofitable to provide liquidity outside of given prices, this can provide significant capital efficiency gains.

{% hint style="info" %}
For example, if an asset has known minting and redemption prices, order flow beyond these prices should always route through the minting and redemption mechanism and so there is no gain to liquidity provision at such prices.

In cases like this, using untruncated trading curves, such as calibrating a Stableswap curve for this situation, leads to a much less efficient outcome as liquidity is implicitly provided at unnecessary prices and thus remains unused compared to the flexibility of an E-CLP.
{% endhint %}

**Efficiency for yield-bearing assets**: E-CLPs boost efficiency on several fronts. In addition to asymmetric concentrated liquidity, E-CLPs build in rate providers. Rate providers make yield-bearing asset pools more efficient by:

* automating liquidity management
* mitigating loss vs rebalancing (LVR)

<figure><img src="../../.gitbook/assets/Rate-providers-v8.gif" alt=""><figcaption><p>E-CLP rate providers make yield-bearing asset pools more efficient by automating liquidity management and mitigating LVR.</p></figcaption></figure>

**Benefits of E-CLPs for Gyroscope**: The capital efficiency gains of the E-CLP are particularly large for GYDGyro tradingMoney mMarket pools, which pair GYD with other assets. GYD should normally trade between the minting price of $1 and the redemption price. In most cases, GYD should trade near $1. In niche situations, however, like under contingency pricing in the DSM, the redemption price may be at a discount. An E-CLP can be calibrated for this precise liquidity profile bounded by minting and redemption prices. In comparison, a Stableswap pool would reserve half of its liquidity for prices above $1 whereas such liquidity is unnecessary.

The E-CLP parameterization displayed above effectively reserves some liquidity for price ranges that may occur, but are less common, but only targeted where it is actually needed.

{% hint style="info" %}
Looking at, for example, Liquity’s LUSD or Lido’s stETH (1) the minting price roughly equates the upper price bound and (2) the redemption price roughly equates the lower price bound.

For these assets it would thus be desirable to focus liquidity on the price range between these two soft price-bounds. In these settings, an E-CLP would provide capital efficiency gains over Stableswap pools for these asset pairs.
{% endhint %}

Notably, there is always some cost to minting/ redemption operations, be it operational (gas costs of mint/ redeem txs) or fundamental (opportunity costs, ‘educational costs’, or other). This premium can be roughly incorporated in defining the price bounds.

## Risks of E-CLPs

Using E-CLPs also comes with certain risks, including smart contract risk, strategy risk, and adverse selection risk. For a more comprehensive description of risks, please refer to terms of service or similar document governing your chosen user interface, as well as review the code available here.

**Smart contract risk:** As with any smart contract, there is an inherent risk that an exploit or bug puts deposited assets at risk. This risk can be reduced by conducting code audits and testing it, but it can not be fully mitigated, especially because E-CLPs are a novel concept and experimental technology. The code audit covering an implementation of E-CLPs can be viewed [here](../audit-reports.md).

**Strategy risk:** By entering into the pool, LPers commit to a market making strategy, and in turn a portfolio rebalancing rule, that fundamentally has different payoffs than just holding the underlying assets or using a different rebalancing rule. The portfolio rule of an E-CLP LP position depends on the parameterization of the pool. LPs should independently consider the given portfolio rule and pool parameters.

**Adverse selection risk:** In any AMM pool, if the true relative market price between assets in the pool jumps permanently, LPers incur a loss due to adverse selection. In particular, the pool is left offering 'stale' quotes at worse than true market price. The adverse selection loss will be equal to the profit to arbitrageurs for moving the pool's quoted price back into equilibrium with the rest of the market.

## Technical Specification

All of the most important functions are defined in the file GyroECLPMath.sol and listed in the below table.

<table><thead><tr><th width="374">Function</th><th>Purpose</th><th data-hidden></th></tr></thead><tbody><tr><td>calculateInvariant</td><td>(Re-)computes the invariant r from the current reserves t = (x, y)</td><td></td></tr><tr><td>calcOutGivenIn </td><td>Computes the amount that leaves the pool when a certain amount enters it, after fees.</td><td></td></tr><tr><td>calcInGivenOut</td><td>Computes the amount that needs to enter the pool when a certain amount should leave it, after fees. </td><td></td></tr><tr><td>calcXGivenY</td><td>Computes the amount of asset x given a certain amount of asset y and a certain invariant. Used by calcOutGivenIn and calcInGivenOut. </td><td></td></tr><tr><td>calcYGivenX</td><td>The same functionality for y given x. </td><td></td></tr><tr><td>liquidityInvariantUpdate</td><td>New invariant when liquidity is added/removed in a “balanced” fashion (without affecting the price). This avoids fully re-calculation of the invariant.</td><td></td></tr></tbody></table>

Conceptually, the ‘ellipse’ function is derived from transforming a circle with stretch, rotation, and displacement. The E-CLP invariant can be described as the minor radius (also known as the “semi-minor axis”) of the ellipse.

To read about the mathematical specification and implementation, see the below resources:

{% embed url="https://docs.gyro.finance/gyroscope-protocol/technical-documents" %}

### Reading E-CLP parameters

In order to retrieve information about an individual E-CLP calibration, it is possible to query getECLPParams, which returns two tuples.

* The first tuple returns int256 (signed) values for: alpha, beta, c, s, lambda
* The second tuple is the output of an off-chain computation that is based on the first tuple and can be referenced/ proven if desired. This tuple contains auxiliary variables used in high-precision calculations, in order: tauAlpha, taubBeta, u, v, w, z, d^2.

The various parameter values can be understood as follows:

* α (alpha) defines the lower bound of the price range
* β (beta) defines the upper bound of the price range
* c, s define the rotation point and are further defined by the cosine (respectively sine) of the rotation angle.
* The price of maximum liquidity is the quotient s/c (which is also the tangent of the rotation angle).
* λ (lambda) defines the stretching factor. The higher λ, the more liquidity is concentrated within the price range. For lower λ, the pool’s liquidity is more evenly spread across the price range. Geometrically, a higher λ means that the ellipse is more elongated, with λ = 1 corresponding to a circle.

<figure><img src="https://lh7-us.googleusercontent.com/7Mvl_CtmYuy9WFjhKT7TsXZvpNowu2tJRJ7-kCdeZvvPhuPnt5Iyr5S1afs_R04MVUe5x2ghEQJ22YJhDLYKTMAQ6z-K0QxnrTL4S2Gt3uK-UuICiqgbhND3C3JnGVb123hKuJrbKZwv-8dfxB9WN6I" alt=""><figcaption><p>Intuition on E-CLP construction</p></figcaption></figure>

{% hint style="info" %}
Note, the ordering of the two tokens (“token0” and “token1”) follows from the lexicographical order of the contract address - as required by the Balancer Vault. For example, comparing the addresses “A0b8\[..]” and “e07F\[..]” , the address starting with “A0b8” would be Token0, the address starting with “e07F” would be Token1.

For ease of reading, calibrations are typically denoted with GYD as token0 and the other asset as token1. Whenever Balancer’s rules prohibit this (and require that GYD is token1), the parameters need to be “flipped” as follows: alpha' := 1/beta, beta' := 1/alpha, s’ = c, c’ = s.
{% endhint %}

### Notes

For further detail and the underlying mathematical operations, see:

\[1] StableSwap, Curve, available at: https://curve.fi/files/stableswap-paper.pdf
