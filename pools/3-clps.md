---
description: Cubic-Concentrated Liquidity Pools or 3-CLPs
---

# 3-CLPs

## Description of 3-CLPs

**Cubic CLPs, or 3-CLPs, concentrate the liquidity of three assets to a pricing range.** The first 3-CLPs are designed for symmetric price ranges \[α,1/α] on the three asset pairs in the pool. A given pool is parameterized by the pricing parameter α and the three assets that make up the pool [\[1\]](3-clps.md#notes).

{% hint style="info" %}
Given quantities of real reserves (x,y,z) in the pool and the pool's pricing parameter α, the offset a can be calculated [\[2\]](3-clps.md#notes). This offset describes the amount the pool adds to real reserves to form the virtual reserves that achieve the pricing range.&#x20;

Symmetric 3-CLPs use the following invariant: (x+a)(y+a)(z+a) = L^3
{% endhint %}

Like in any Balancer or Curve pool with more than two assets, the prices between different pairs of assets in the 3-CLP interact. For example, if asset x is traded against asset z, the pool’s spot price of asset y vs asset z is going to change. An implication of this is that the combinations of prices that are simultaneously offered by the pool at any point in time are constrained by a mathematical relationship.

**Because of this relationship, understanding the multi-dimensional pricing bounds of the 3-CLP requires some thought.** For the 2-CLP, the pricing bounds of the pool are very easy to understand: they are simply an interval of prices on a line, as shown below.

<figure><img src="https://lh6.googleusercontent.com/GbUtkQtQ-tuoYYkFyDMfDZv3gVtmrDXwxw9TjO74o2uW9N1Laes-2XpOS68S8NIeTtH0V0jry-IRwlmI2I5W36_SxgX_5oImxrsMvyjhwYD50ImQ-UddNM2ua0hq4Bzk26cmEJpfvke-MRBF8N6tp3Q" alt="stylistic visualization of 2-CLP price bounds"><figcaption><p>stylistic visualization of 2-CLP price bounds</p></figcaption></figure>

**The graphic below visualizes the feasible pricing region of a 3-CLP, which is the region of spot prices that a 3-CLP may quote.** Here we chose α=0.5, so that the pool does not price below 0.5 or above 2.0.

<figure><img src="https://lh6.googleusercontent.com/RBCkNsxzRrF7UbF74qSSNoa99_AjVg2HRyZhJ3xR4WeOjaxGoWxMPuz2vX2W_1gAGqc7LARkrcwjOGyxGMROvcwNpbBFI7PStehE4Aa8IfFgOfubFnDqRUs1gKqzCck7-uj16n7MOfwozAaKxx6EVWA" alt="stylistic visualization of the feasible pricing region of a 3-CLP"><figcaption><p>stylistic visualization of the feasible pricing region of a 3-CLP</p></figcaption></figure>

The feasible pricing region is parameterized by the prices of asset x and y, respectively, denoted in units of asset z. The third price pair, of x denoted in units of y, is the quotient of the two prices: px/y=px/z/py/z. In the figure, each included asset is represented with a different color.&#x20;

The lines indicate price combinations where the respective reserve asset x, y, or z is exhausted in the pool, and the shaded regions indicate where the respective reserve asset has a positive balance in the pool.&#x20;

The region where all colors overlap is the feasible pricing region - these are combinations of prices that the pool can quote. At the corner points, the pool only holds a single asset and two of the three asset pairs realize either the minimum or the maximum price bound (i.e., they are equal to α=0.5 or 1/α=2.0) [\[3\]](3-clps.md#notes). Further documentation is available here.

## Benefits of 3-CLPs

**3-CLPs amplify the benefits of 2-CLPs:**

* _**Capital efficiency**:_ By concentrating liquidity between three assets, 3-CLPs achieve a 50% capital efficiency improvement from aggregating the third asset compared to a similar setup of trading pairs as 2-CLPs.&#x20;
* _**Gas efficiency**_: Trading among three assets is more gas efficient than connecting two trades through two different 2-CLPs.&#x20;
* _**User experience**_: 3-CLPs remain comparatively simple in architecture and user experience.

<figure><img src="../.gitbook/assets/3-CLP-v4 (1).gif" alt="Stylized representation of capital efficiency gains of 3-CLPs"><figcaption><p>Stylized representation of capital efficiency gains of 3-CLPs</p></figcaption></figure>

## Risks of 3-CLPs&#x20;

**Using 3-CLPs also comes with certain risks, including the following.** These risks include those of the 2-CLPs; we only explain these risks briefly. See the section on 2-CLPs for further details.

* _**Smart contract risk**_: the risk that an exploit or bug puts deposited assets at risk.&#x20;
* _**Strategy risk**_: the risk that the portfolio strategy implied by the pool has worse payoffs than a different strategy (such as just holding the assets).&#x20;
* _**Adverse selection risk**_: the risk that permanent price changes imply a loss to LPers because arbitrageurs take stale price quotes.

**Compared to a 2-CLP, LPers in a 3-CLP are exposed to additional risks:**&#x20;

* _**Asset interaction risk:**_ since the 3-CLP contains an additional asset, LPers are exposed to strategy and adverse selection risk due to two additional price pairs.&#x20;

{% hint style="info" %}
For example, if the price of one of the assets drops to a sufficiently low level, the pool will end up with only that least valuable asset (see the figure above). This phenomenon occurs in many multi-asset AMMs, such as the Curve stablecoin 3-pool. Just like strategy risk in the 2-pool, it can be reduced by choosing fundamentally connected assets and appropriate price bounds.
{% endhint %}

* Note that the pricing region of the 3-CLP is more complex than for other pools; this may mean that arbitrageurs need more time to get familiar with the functioning of the pool before it runs smoothly.

## Technical Specification

To read about the mathematical specification and implementation, see the below resources

{% content-ref url="../gyd/technical-documents.md" %}
[technical-documents.md](../gyd/technical-documents.md)
{% endcontent-ref %}

## Notes

\[1] For technical reasons, the parameter provided to the smart contract is $$\sqrt[3]{\alpha}$$ instead of α itself.

\[2] The offsets are computed as $$a = L \sqrt[3]{\alpha}$$

\[3] The figure is asymmetric, with the curve for z having a different shape than the curves for x and y, because we chose to express the relative pool prices in terms of asset z. This is only a property of how the figure was made and does not affect the functioning of the pool; within the pool, the three assets take on symmetric roles.
