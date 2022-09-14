---
description: Market- & pricing structure
---

# Autonomous pricing

Gyroscope uses **two different automated market types:**

* a **Primary-market AMM** (PAMM) design to quote mint and redeem prices of stablecoin units, while accounting for potential shocks to underlying assets
* multiple **Secondary-market AMMs** (SAMMs) that concentrate liquidity within the price bounds of the PAMM by customizing Balancer v2 pools

{% hint style="info" %}
The terminology of the “primary- and secondary market” is borrowed from traditional finance where the primary market refers to the ‘issuing market’ and the secondary market refers to the ‘trading market’ (e.g., in ETFs).
{% endhint %}



## Interplay of markets

The SAMMs each concentrate liquidity at ranges provided by the PAMM for reserve asset-Gyroscope stablecoin pairs. These provide guarantees on highly liquid paths in and out of Gyro stablecoins. The SAMMs are also independent from each other: if the paired asset in a SAMM fails, then the remaining SAMM pools can still function, unlike one common AMM pool today. The SAMMs will form the center of a network of connecting pools that will allow efficient routing of trades. Some Gyroscope reserve vaults will deploy assets into pools that augment this network, and other existing AMM pools will connect with paired assets in the SAMMs.

![](<../../../.gitbook/assets/SAMM and Reserve Pools Graphic.png>)

A feature of this design is that it induces a peg coordination mechanism, which fosters high liquidity around the peg, while curtailing speculative attacks and bank run effects with a circuit breaker in case coordination breaks.
