---
description: >-
  CLPs are a class of AMMs that price the exchange of assets within a defined
  range
---

# Concentrated Liquidity Pools

## Description

Gyroscope’s ‘Concentrated Liquidity Pools’ (CLPs) are a class of Automated Market Makers (AMMs) that price the exchange of assets within a defined range. As such, any CLP only provides liquidity for trading activity restricted to this specific region. The goal is to use the pool’s capital efficiently. It is expected that most reserve assets will be stored in CLPs.

**This design has several **_**benefits**_** - as described below. CLPs are currently built on Balancer and include pools with two or three assets:**

* _**Pools with two assets**_ - aka Quadratic-CLPs or [2-CLPs](2-clps.md), named after the quadratic invariant curve - are similar to Uniswap v3’s concentrated liquidity pools. But unlike Uniswap, a 2-CLP effectively offers a ‘single tick’, where liquidity is distributed evenly across a single active trading range.

{% hint style="info" %}
2-CLPs are best understood as a simplified design of Uniswap v3. Specializing the design for the most-traded ranges of included assets enables a pool with (i) high capital efficiency, (ii) high gas-efficiency, and (iii) a simple user-experience.
{% endhint %}

<figure><img src="../../.gitbook/assets/2-clp-v2 (2).gif" alt="Stylized representation of capital efficiency gains of 2-CLPs"><figcaption><p>Stylized representation of capital efficiency gains of 2-CLPs</p></figcaption></figure>

* _**Pools with three assets**_ - aka Cubic-CLPs or [3-CLPs](3-clps.md) support three assets and are functionally best understood as an extension of 2-CLPs. As a high-level summary, they amplify the benefits of 2-CLPs.

{% hint style="info" %}
An intuitive way of thinking about 3-CLPs is to imagine a pool that combines two of the most impactful AMM innovations into one: multi-asset pools and concentrated liquidity.
{% endhint %}

<figure><img src="../../.gitbook/assets/3-CLP-v4.gif" alt="Stylized representation of capital efficiency gains of 3-CLPs"><figcaption><p>Stylized representation of capital efficiency gains of 3-CLPs</p></figcaption></figure>

* _**E-CLPs**_ - aka [Elliptic-CLPs](./)[ ](e-clps.md)support asymmetric concentrated liqudity for two assets. They provide a new type of concentrated liquidity that allows highly flexible and asymmetric liquidity profiles in a single pool position.

<figure><img src="../../.gitbook/assets/E-CLP-liquidity-density-animated-chart-v6.gif" alt=""><figcaption><p>The E-CLP's asymmetric concentrated liquidity improves capital efficiency over StableSwap by putting liquidity only where it is needed.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Rate-providers-v8.gif" alt=""><figcaption><p>E-CLP rate providers make yield-bearing asset pools more efficient by automating liquidity management and mitigating LVR.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Boosted-E-CLPs (1).gif" alt=""><figcaption><p>Rehype pools combine multiple yield sources in a single pool.</p></figcaption></figure>

## **Users of CLPs**

**Stakeholders can use the Gyroscope CLPs in different, yet mutually beneficial ways:**

* _**Gyroscope reserve**_**:** Gyroscope reserve assets will be deployed to some CLPs. Fee revenue from reserve assets deployed to CLPs will increase the protocol collateralization ratio.
* _**Direct LPs**_**:** As CLPs will hold protocol assets, they will likely offer substantial liquidity. However, CLPs also remain open to any liquidity provider. Any direct LP’ers can access bootstrapped pools that offer deep liquidity for the most-commonly traded ranges with volume (and in turn LP fee revenue) channeled through Balancer’s Smart Order Routing.
* _**Mutually-beneficial cycle:**_ The two uses of CLPs benefit each other. (i) Once reserve assets are deployed, LPers benefit from having substantially bootstrapped pools with high capital efficiency. This increases pool activity and thus fee revenue. (ii) The Gyroscope protocol, in turn, benefits as a small fraction of the revenue of CLP LPs may be captured via a protocol fee. (iii) The interplay between LPers and deployed reserve assets creates economies of scale that positively impact pool activity.
