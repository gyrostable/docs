---
description: Market- & pricing structure
---

# Autonomous pricing

Gyroscope uses **two different automated market types:**

* a **Dynamic Stability Mechanism** (DSM) design to quote mint and redeem prices of stablecoin units, while accounting for potential shocks to underlying assets
* multiple **GYD Trading Pools** that concentrate liquidity within the price bounds of the PAMM by customizing Balancer v2 pools

{% hint style="info" %}
It is also possible to think about this market structure with terminology from traditional finance. Accordingly, the DSM would be the primary, or issuing, market and the Gyro Money Markets would be the secondary, or trading, market.&#x20;
{% endhint %}

## Interplay of markets

The GYD Trading Pools each concentrate liquidity at ranges provided by the DSM for reserve asset-Gyroscope stablecoin pairs. These provide guarantees on highly liquid paths in and out of Gyro stablecoins. The GYD Trading Pools are also independent from each other: if the paired asset in a GYD Trading Pool fails, then the remainingGYD Trading Pools can still function, unlike one common AMM pool today.&#x20;

The GYD Trading Pools will form the center of a network of connecting pools that will allow efficient routing of trades. Some Gyroscope reserve vaults will deploy assets into pools that augment this network, and other existing AMM pools will connect with paired assets in the GYD Trading Pools.

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Stylized overview of relevant Gyroscope markets</p></figcaption></figure>

A feature of this design is that it induces a peg coordination mechanism, which fosters high liquidity around the peg, while curtailing speculative attacks and bank run effects with a circuit breaker in case coordination breaks.
