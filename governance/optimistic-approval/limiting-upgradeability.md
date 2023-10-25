---
description: An implementation of an Optimistic Approval mechanism
---

# Limiting Upgradeability

## All users, not just governors, should have a say

Through an additional mechanism, end users of the protocol - GYD stablecoin holders - have  power over governance regarding how upgradeable the protocol should be. This takes the form of an alternative 'wrapped' form of GYD, boundedGYD.

As implemented in `WrappedERC20WithEMA`, at any time, a user can choose between holding GYD or the wrapped bGYD and can freely convert between them. Choosing to hold bGYD means voting for limited protocol upgradeability.&#x20;

When a user converts between GYD and bGYD, a moving average is updated in the bGYD contract. When the moving average exceeds a threshold in addition to the total bGYD supply exceeding another threshold, upgradeability of core Gyroscope contracts through governance becomes more difficult. This takes the form of increased difficulty in action tiering.

The main idea is to let the end-user decide when the system should be more upgradeable and when core infrastructure should be considered more settled based on the market choice of whether to adopt GYD or bGYD. This change of adoption is intentionally difficult (e.g., integrations would have to shift to using bGYD) because early on the DeFi space itself is not settled and any stablecoin will likely need to adapt parameters and structure over time as DeFi itself changes.

**Tracking the Moving Average**

We track the moving average of the share of bGYD to GYD in terms of an irregularly-spaced exponential moving average (EMA) as follows. Index the points in time where the EMA is updated by $$i$$, where $$i=0$$ marks deployment of the contract. Let $$t_i$$be the block height at time index $$i$$, and let $$x_i := \text{bGYD supply}/\text{GYD supply}$$ at the end of block $$t_i$$. Let $$y_i$$be the EMA at time index $$i$$. We can define the EMA as

$$
\begin{align*} y_0 &= 0 \\ y_{i} &= y_{i-1} + K_i \cdot (x_i - y_{i-1}) \quad\text{if $i > 0$} \\ \text{where } K_i &= 1 - e^{-(t_{i} - t_{i-1}) / \tau}. \end{align*}
$$

Here, $$\tau$$ is a constant (i.e., a parameter to the contract) that is usually interpreted as the width of a time window. Observe that, if the spacing of the $$x_i$$ time series was regular, then all the $$K_i$$ would be equal, but in our case, this does not hold. The definition of $$K_i$$ is motivated by the continuous form of the EMA from signal processing, see [here](https://stackoverflow.com/a/1027808/266614).

Note that we only track the EMA at the _previously updated block_, not the current block. This is to prevent manipulation of the EMA by, e.g., using a flash loan. The values $$x_i$$ and $$t_i$$ in the above formulas therefore refer to the most recently-observed values that are not from the current block; the current-block values are not used to update the current-block EMA, but will only be used in the next block.

The variables in `_updateEMA()` match the variables from the formulas above as follows:

<table><thead><tr><th width="127">Math</th><th>Code</th></tr></thead><tbody><tr><td><span class="math">y_{i-1}</span></td><td><code>expMovingAverage.value</code></td></tr><tr><td><span class="math">x_i</span></td><td><code>previousWrappedPctOfSupply.value</code></td></tr><tr><td><span class="math">t_{i-1}</span></td><td><code>expMovingAverage.blockNb</code></td></tr><tr><td><span class="math">t_i</span></td><td><code>previousWrappedPctOfSupply.blockNb</code></td></tr><tr><td><span class="math">\tau</span></td><td><code>windowWidth</code></td></tr></tbody></table>



## Optimistic approval

Limiting upgradeability in this way is an application of the idea of Optimistic Approval, a new governance primitive that allows governance changes to be conditional on a timelock and veto process. It is a very flexible mechanism that can be used both to streamline governance processes and to better align incentives among protocol participants, not just in Gyroscope but also in DeFi governance more broadly.

Read our research piece introducing Optimistic Approval [here](https://ournetwork.substack.com/p/our-network-deep-dive-2).

Optimistic Approval can help to align incentives among different types of parties: one who possesses governance powers (governors), and another (guardians) who has the power to optionally veto during a timelock period. Ordinarily, guardians do not need to be involved in day-to-day governance, but the veto gives them the ability to block malicious proposals that would deviate from the vision of the protocol.

The Optimistic Approval framework generalizes who has governing powers and who has veto rights during a time delay. Additionally, the mechanism is parameterized by (1) initial timelock duration, (2) guardian voting threshold for increasing timelock duration, and (3) guardian voting threshold for achieving veto.

In this first application to Gyroscope in the form of limiting upgradeability, Optimistic Approval is designed to give protocol users a veto power to stop governance changes that they disagree with. In this case, protocol users fulfil the guardian role of stewarding the protocol vision (e.g., of maintaining stability). The mechanism introduces checks and balances on governors' power. Should governors try to deviate from the shared vision of the protocol, Gyro Dollar holders will be able to exercise optional veto powers during the time delay to stop it. Ordinarily, Gyro Dollar holders will not need to do anything if governance actions are sound. However, if governance actions are contentious, Gyro Dollar holders can exercise the veto to block the action.

{% hint style="info" %}
Optimistic Approval was initially devised this application as a means to circumvent an impossibility conjecture around secure decentralized governance arising from the models in our [Stablecoins 2.0 paper](https://arxiv.org/abs/2006.12388) (Conjecture 1).
{% endhint %}

