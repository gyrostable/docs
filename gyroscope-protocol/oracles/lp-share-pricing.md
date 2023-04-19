---
description: Methodology and implementation of pricing LP share tokens
---

# LP share pricing

To price LP tokens, it is not enough to simply add the values of all assets in the pool as this is easily manipulated. Instead, a more robust procedure is required to calculate LP token values.

{% hint style="info" %}
The precise instructions on how to calculate LP shares of the 2-CLP, 3-CLP, or E-CLP are available in section 5 of this [technical paper](https://github.com/gyrostable/technical-papers/blob/main/Consolidated%20Price%20Feed%20and%20Circuit%20Breakers/Design%20of%20the%20Consolidated%20Price%20Feed%20and%20Circuit%20Breaker%20System.pdf).&#x20;
{% endhint %}

## Example: Constant Product Pools

This example demonstrates the principles of robust LP share pricing applied to constant product pools.

For a given constant product Balancer pool containing assets 1, ..., n, define the following:

$$
w_i = \text{weight of asset } i \\
r_i = \text{amount (in \# tokens) of asset } i \\
p_i = \text{price of asset } i \\
S = \text{total \# LP tokens}
$$

The constant product invariant of the pool is

$$
L = \prod_{i=1}^{n} r_i^{w_i}
$$

Note that the amounts $$r_i$$are easily manipulatable through swaps, but the product $$L$$is not. And, as we require asset pricing oracles elsewhere, we can presume that the prices $$p_i$$ are also not easily manipulatable (controls to assure against this will be discussed elsewhere).

To calculate a manipulation-resistant LP token price, it will be enough to express the pricing of LP tokens solely in terms of manipulation-resistant variables $$w_i, p_i, L / S$$. Note that while $$L$$ and $$S$$ are individually manipulatable by adding or removing liquidity, $$L/S$$ is not easily manipulatable as long as proper accounting methods are in place for handling adding and removing of liquidity (see Section 5.5 in the [technical paper](https://github.com/gyrostable/technical-papers/blob/main/Consolidated%20Price%20Feed%20and%20Circuit%20Breakers/Design%20of%20the%20Consolidated%20Price%20Feed%20and%20Circuit%20Breaker%20System.pdf) for more details).

The portfolio value of the entire pool can be calculated as

$$
\text{Pool value} = L \prod_{i=1}^n \left( \frac{p_i}{w_i} \right)^{w_i}
$$

**In turn, the LP token price can be calculated in terms of manipulation-resistant variables as**

$$
p_{\text{LP token}} = \frac{\text{Pool value}}{S} = \frac{L}{S} \prod_{i=1}^n \left( \frac{p_i}{w_i} \right)^{w_i}
$$





## Pricing LP tokens for 2-CLPs, 3-CLPs, and E-CLPs

LP share pricing for the CLPs follows the same general principles and is described in full detail in Section 5 of the following technical paper.

{% embed url="https://github.com/gyrostable/technical-papers/blob/main/Consolidated%20Price%20Feed%20and%20Circuit%20Breakers/Design%20of%20the%20Consolidated%20Price%20Feed%20and%20Circuit%20Breaker%20System.pdf" %}
