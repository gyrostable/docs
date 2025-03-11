---
description: Stratifying reserve assets to build resilience
---

# Reserve design

## Design philosophy

The Gyroscope reserve is designed to maximize the resilience of the stablecoin system. This requires that risks are 'stratified', or isolated from each other. Losses that accrue in one sub-system should never spill over into other connected sub-systems.

{% hint style="info" %}
To illustrate why this is important, consider that, for example, LP positions in the Y Curve pool take on the composed risks of USDT, Dai, USDC, TUSD, Compound, Aave, and Curve. Due to the design of a Curve AMM pool, if one of these components were to fail, the value of the whole pool would collapse.​

This is commonly referred to as 'composability risk' or also 'contagion risk'.
{% endhint %}

There are two forms of Gyroscope reserves currently:

* AMOs (algorithmic market operations) hold reserves in GYD pools alongside set amounts of unissued GYD, using specially designed E-CLPs. Issuance and redemption from these reserves are seamless with swaps and helps bootstrap new liquidity. As unissued GYD are bought from these pools, they become issued and enter circulation, backed by the asset that entered the pool.
* DSM (dynamic stability mechanism) reserves enforce extra protections (e.g., diversification rules, oracle protections, and smart contract risk mitigations. DSM reserves are also redeemable but require more sophisticated interaction with the protocol's balance sheet.

In the early growth phase, most reserves are held in AMOs to facilitate growth and liquidity. AMOs can be transitioned into DSM reserves as GYD scales with a balancing level in AMOs.

## Functional implementation

In order to stratify risks, the Gyroscope reserve is separated into lower-level vaults (circles in the figure below). This design is aimed at ensuring that risks are contained within each vault, with little overlap of asset configurations between the vaults.

**This design allows the ‘safe failure’ of an individual vault without creating spillover risks for the remaining vaults.**

If the Gyroscope stablecoin becomes undercollateralized due to a vault failure (i.e., if a circle is removed in the below figure), the Gyroscope system should still be able to remain stable at $1. This is possible due to the autonomous fallback mechanism that uses unaffected reserves and yield generated from reserve assets to support the stablecoin price. Stablecoin price quotes are autonomously adapted based on the reserve quality and the market situation with the goal of long-term sustainability.

If the available funds are not sufficient to cover the total amount of stablecoins outstanding, Gyroscope’s autonomous price quotes stabilize the stablecoin market price and create incentives against runs on the reserves (further described here). This provides an important rationale for speculators to expect a full system recovery and ‘arbitrage’ the stablecoin price.

**The reserve can recover from an under-collateralized state back to full collateralization via several mechanisms:**&#x20;

* _Via yield generated on reserve assets._ For reserve assets deployed to AMM pools, a yield is generated via trading fees.&#x20;
* _Via potential revenue from protocol fees, if so decided by the governance_. There might be two protocol fees in Gyroscope: a small fee for minting/ redeeming stablecoins, as well as a fee on revenue that accrues to LPers of Gyroscope's custom AMM pools (called CLPs).
* _Via a future supply expansion of the stablecoin._ When new stablecoins are minted, the issuance proceeds go completely to the reserve, which also pushes the reserve towards 100% collateralization.

**Gyroscope’s resilience, i.e., its ability to maintain its functionality even if parts of the system fail, and its ability to recover are key elements of the Gyroscope design.** A stylized representation of Gyroscope's initial reserve configuration is shown below.

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Stylized representation of Gyroscope's initial reserve configuration, which may evolve over time.</p></figcaption></figure>

The reserve structure is able to evolve over time as the on-chain asset space evolves. For the purpose of demonstrating reserve stratification principles, a future reserve structure may resemble the following once several newly launched assets reach a larger scale.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>A hypothetical future reserve structure for the purpose of illustrating reserve stratification principles.</p></figcaption></figure>

## Technical implementation

The reserve is implemented as a series of vaults that are designed for risk stratification. Each vault deploys assets according to a strategy decided by decentralized governance. The first vault strategy is deploying assets into Gyroscope's [Concentrated Liquidity Pools](../../pools/concentrated-liquidity-pools.md) (CLPs). This is the only strategy implemented at the moment.

Not only will a significant amount of reserve assets be stored in CLPs, but CLPs are also crucial for building out the liquidity network in the Balancer ecosystem. CLPs are AMM pools that price assets within the pool in a predefined price range. As such, any CLP only provides liquidity for trading activity restricted to this specific region.

Other future vault strategies may include lending pools and delta neutral hedging strategies. When the reserve holds on-chain derivatives, however, it is important to account for the risk in the collateral backing those derivatives (e.g., if they are backed by centralized assets, they will have centralized risk factors).
