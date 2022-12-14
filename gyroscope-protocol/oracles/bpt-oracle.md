---
description: Methodology and implementation of Balancer Pool LP token (BPT) pricing
---

# BPT Oracle

{% hint style="info" %}
The LP share pricing on this page describes constant product pools (ordinary Balancer pools). Coming documentation will describe how to similarly price a wide variety of other LP tokens.
{% endhint %}

To price LP tokens, it is not enough to simply add the values of all assets in the pool as this is easily manipulated. We use a more robust procedure for calculating Balancer LP token values.

For a given Balancer pool containing assets 1, ..., n, define the following:

$$
w_i = \text{weight of asset } i \\
r_i = \text{amount (in \# tokens) of asset } i \\
p_i = \text{price of asset } i \\
S = \text{total \# BPT tokens}
$$

The constant product of the Balancer pool is

$$
k = \prod_{i=1}^{n} r_i^{w_i}
$$

Note that the amounts $$r_i$$are easily manipulatable, but the product $$k$$is not. And, as we require asset pricing oracles elsewhere, we can presume that the prices $$p_i$$are also not easily manipulatable (controls to assure against this will be discussed elsewhere).

To make the manipulation-resistant BPT oracles, it will be enough to express the pricing of BPT tokens in terms of solely manipulation-resistant variables $$w_i, p_i, k, S$$.

The portfolio value of the Balancer pool can be calculated as

$$
\text{BPT total value} = k \prod_{i=1}^n \left( \frac{p_i}{w_i} \right)^{w_i}
$$

Then, in turn, the BPT price can be calculated as

$$
p_{BPT} = \frac{\text{BPT total value}}{S} = \frac{k \prod_{i=1}^n \left( \frac{p_i}{w_i} \right)^{w_i}
}{S}
$$
