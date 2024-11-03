---
description: >-
  Arguably the most capital efficient pools, these E-CLPs combine asymmetric
  concentrated liquidity with auto-rehypothecation to lending markets.
---

# Rehype E-CLPs

<figure><img src="../../.gitbook/assets/Boosted-E-CLPs.gif" alt=""><figcaption><p>Rehype pools combine several yield sources into a single pool.</p></figcaption></figure>

## Description of Rehype E-CLPs

Gyroscope’s Rehype pools increase LP yields by combining asymmetric concentrated liquidity with auto-rehypothecation to lending protocols, improving capital efficiency on two fronts. They allow LPs to triple dip in yield sources by layering swap yields from concentrated liquidity on top of lending yields on top of token incentive markets.

Rehype pools work by incorporating lending deposits like Aave aUSDC in a simple way directly at the pool asset level with the conversion between lending deposit and underlying asset handled through front-ends and smart order routing (SOR). Gyroscope’s Rehype pools avoid the complexity of ‘pool on top of pool on top of pool’ architecture. They introduce no new complexity at the smart contract level beyond E-CLPs. Instead, they handle the complexity at the more flexible layers of SOR and front end design. This makes the pools comparatively safer than alternative pool designs, as the Rehype pools inherit the safety record of E-CLPs and only add in Aave risks.

Rehype pools combine many yield sources into one form that can itself be used as productive collateral in other protocols in the form of pool shares. At the same time, rehypothecation in these pools is transparent and user controlled, in contrast to common rehypothecation practices that give issues in TradFi.

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption><p>Rehype pools combine many yield sources into one</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Order-Routing-in-Rehype-Pools.gif" alt=""><figcaption><p>How Rehype pools route orders in underlying assets.</p></figcaption></figure>

## GYD and Rehype Pools

​​GYD Rehype pools enable the scaling of more robust risk-adjusted yield sources for a decentralized stablecoin in a market that is increasingly dominated by centralized actors. They layer decentralized yield sources on top of each other, removing opportunity costs to lower the cost of capital for GYD liquidity.

## Risks of Rehype E-CLPs

Using Rehype E-CLPs comes with certain risks, including the risks of E-CLPs (smart contract risk, strategy risk, and adverse selection risk covered [here](e-clps.md)) and rehypothecation risk (e.g., risks of Aave). Note that Rehype pools work with a simple, modular design that is aimed to minimize smart contract risk and doesn’t introduce new smart contract code for the rehypothecation.

**Rehypothecation risk:** By entering into the pool, LPers commit to a strategy of deploying their LP assets to a lending protocol (e.g., Aave). Lending protocols like Aave have their own risks, including smart contract risks, liquidity risks, insolvency risks, oracle risks, and governance risks. Lending protocol risks may also be different on different chain deployments. For example, the level of liquidity in Aave on a particular chain impacts the liquidity LPers have to withdraw to underlying assets, although withdrawal to Aave deposit tokens is unaffected by this.

Like every innovative project in DeFi, users  should do their own research and assess for themselves the riskiness of the relevant Aave lending markets. Rehype pools make everything fully transparent on-chain and give users control over their strategy selection.
