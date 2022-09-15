---
description: Quadratic-Concentrated Liquidity Pools or 2-CLPs
---

# 2-CLPs

## Description of 2-CLPs

**Gyroscope’s 2-CLPs are AMMs that concentrate liquidity within a pricing range.** A given 2-CLP is parameterized by the pricing range \[α,β] and the two assets in the pool **** [\[1\]](2-clps.md#notes).

Given quantities of real reserves (x,y) in the pool and the pool’s pricing range \[α,β], offsets a and b can be calculated [\[2\]](2-clps.md#notes). These offsets describe the amount the pool adds to real reserves to form the virtual reserves that achieve the pricing range. These pools use the following invariant: (x + a)(y + b) = L^2.

**2-CLPs can also be represented visually.** The conceptual graphic below shows a constant product curve without concentrated liquidity where two price bounds are depicted as blue rectangles. A 2-CLP can be understood as “zooming into” the part of the curve between the price bounds. Here, the curve is substantially ‘flatter’ with trades having less price impact. Further documentation is available here.

![conceptual graphic showing liquidity concentration of 2-CLPs](https://lh3.googleusercontent.com/HiTLnGO8aQoWhypPUi87DmLyJCBsbL2ra71HxO98w2JVsPV1-ZoPKYlp9zskMvxrnHWes5e4RzNhFnDEPgl5eX\_NmzvCm88Xq4AO5rm\_C6sTnj0YiHevV-d5Sgb-\_n1xxFBe4LEBFYtDTAsBfAK6dv8)

**Compared with “x \* y = k” (i.e., constant product or Uniswap v2) AMMs, a 2-CLP can better utilize the existing liquidity.** Instead of spreading liquidity across the entire range of prices that could in theory occur - ‘from zero to infinity’ - _a 2-CLP focuses on a small range of prices by adding price bounds_ which are implemented using ‘virtual reserves’. Virtual reserves can be understood as the reserves that would be necessary to reach the depth of a concentrated liquidity position using a standard unlimited range pool.

![Stylized representation of capital efficiency gains of 2-CLPs](<../../.gitbook/assets/2-clp-v2 (3).gif>)

{% hint style="info" %}
The notion of virtual reserves was first introduced in the YieldSpace whitepaper [\[3\]](2-clps.md#notes) and Uniswap v3 first introduced the concept of concentrated liquidity pools [\[4\]](2-clps.md#notes).&#x20;

2-CLPs are best understood as a simplified design of Uniswap v3 that is tailored to a specific use-case. Specializing the design for the most-traded ranges of included assets enables a pool with (i) high capital efficiency and (ii) high gas-efficiency.&#x20;
{% endhint %}

## Benefits of 2-CLPs

**2-CLPs offer three main benefits - capital efficiency, gas efficiency, and a simplified user experience:**

_**- Capital efficiency**_**:** 2-CLPs improve capital efficiency of the Balancer ecosystem. 2-CLPs offer capital efficiency comparable to Uniswap v3 for Balancer pools.

_**- Gas efficiency**_**:** 2-CLPs are designed to be highly gas-efficient. 2-CLPs adopt the efficiently-computable constant-product pricing formula [\[5\]](2-clps.md#notes). 2-CLPs are also designed to integrate with Balancer. Balancer v2 allows composing trades between several pools in a highly gas-efficient manner, laying the foundation for Balancer’s Smart Order Routing [\[6\]](2-clps.md#notes).

_**- User experience**_: 2-CLPs are designed to be as simple as possible. The 2-CLPs design can be considered a specialized variation of Uniswap v3, as the full generality of Uniswap v3's tick system is not always needed. This enables a simpler pool architecture and is reflected in a less-demanding user experience of providing liquidity.&#x20;

## Risks of 2-CLPs&#x20;

**Using 2-CLPs also comes with certain risks, including smart contract risk, strategy risk, and adverse selection risk.**  The term “impermanent loss” is sometimes used as an umbrella term for both strategy risk and adverse selection risk.

_**- Smart contract risk:** _ As with any smart contract, there is an inherent risk that an exploit or bug puts deposited assets at risk. This risk can be reduced by conducting code audits and testing it, but it can not be fully mitigated.&#x20;

_**- Strategy risk:**_ By entering into the pool, LPers commit to a market making strategy, and in turn a portfolio rebalancing rule, that fundamentally has different payoffs than just holding the underlying assets or using a different rebalancing rule. As prices change, the pool sells one asset in exchange for the other [\[7\]](2-clps.md#notes). In an extreme case, the relative price between the two pool assets moves permanently out of the price range. In that case, the pool is left with only the less valuable asset.&#x20;

{% hint style="info" %}
For the CLPs, this strategy risk can be higher than for a pool without concentrated liquidity because the strategy allows more trading at any price within the pool's price range.&#x20;

This is a side effect of capital efficiency and low price impact for traders. In an extreme case, when the value of one of the assets goes to 0, the value of the pool goes to 0 as well. The strategy risk can be reduced by choosing fundamentally related assets for the two sides of the pool (because then severe permanent shifts in relative prices are less likely and oscillations are more likely) and by carefully selecting price ranges [\[8\]](2-clps.md#notes).&#x20;
{% endhint %}

_**- Adverse selection risk:** _ In any AMM pool, if the true relative market price between assets in the pool jumps permanently, LPers incur a loss due to adverse selection. In particular, the pool is left offering 'stale' quotes at worse than true market price. The adverse selection loss will be equal to the profit to arbitrageurs for moving the pool's quoted price back into equilibrium with the rest of the market.&#x20;

{% hint style="info" %}
For the CLPs, this risk can be higher than for a pool without concentrated liquidity because the CLP design offers deeper markets within the pool's price range.&#x20;

In the case of a price jump, more arbitrage is enabled. If, however, the price later returns to the initial price this loss is not realized and the pool profits from trading fees.
{% endhint %}

## Technical Specification

To read about the mathematical specification and implementation, see the below resources

{% content-ref url="../technical-documents.md" %}
[technical-documents.md](../technical-documents.md)
{% endcontent-ref %}

## Notes

\[1] For technical reasons, the parameters provided to the smart contract are $$\sqrt{\alpha}$$ and $$\sqrt{\beta}$$ instead of α and β directly.

\[2] The offsets are computed as $$a = L / \sqrt{\beta}$$, $$b = L \sqrt{\alpha}$$

\[3] Yield Space,’YieldSpace: An Automated Liquidity Provider for Fixed Yield Tokens’: [https://yield.is/YieldSpace.pdf](https://yield.is/YieldSpace.pdf)

\[4] Uniswap, ‘Concentrated liquidity’, available at: [https://docs.uniswap.org/protocol/concepts/V3-overview/concentrated-liquidity](https://docs.uniswap.org/protocol/concepts/V3-overview/concentrated-liquidity)

\[5] Paradigm, ‘Understanding Automated Market-Makers, Part 1: Price Impact’, available at: https://research.paradigm.xyz/amm-price-impact

\[6] Balancer, ‘Smart Order Router V2’, available at: https://docs.balancer.fi/developers/smart-order-router

\[7] Technically, the pool doesn't ‘sell’ any assets, but merely offers them for sale.

\[8] Note that multiple CLPs with different parameters can be deployed for the same asset pair to allow LPers to choose between different risk levels. In this case, the liquidity in different pools of the same pair can be combined through smart order routing along multiple paths.
