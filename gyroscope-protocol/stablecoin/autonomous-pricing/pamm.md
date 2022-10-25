---
description: Minting and redeeming of stablecoin units
---

# Primary-market AMM

## Overview

Stablecoin units can be minted and redeemed in the primary-market (PAMM).

There is no central issuer. Users can mint and redeem stablecoin units directly against the permissionless Gyroscope system. There is no counterparty.

The shape of the PAMM (i.e., the bonding curves that quote prices to mint/ redeem) is a function of the current reserve ratio and outflows.

### Stylized PAMM redemption curve

The stylized PAMM redemption curve for different reserve ratio levels is shown below, against the example of a 50-50 Uniswap pool.

<figure><img src="../../../.gitbook/assets/Graph 2 v2.png" alt=""><figcaption></figcaption></figure>

### Examples and further explanations

#### Redemptions with collateral close to 100%

If the stablecoin just becomes undercollateralized and starts to trade below par, the redemption curve starts near $1 to enable good liquidity around the peg.&#x20;

#### Redemptions with collateral well below 100%&#x20;

If continued redemptions occur, i.e., the 'outflow' increases, the redemption curve eventually moves to the ‘circuit-breaker phase’. At this circuit breaker, the redemption rate decreases below the actual reserve ratio, at which redemptions are always sustainable.

In that case, the bonding curve of the redemption market provides _**decreasing redemption quotes**_ as a circuit breaker. The goal is to disincentivize runs and attacks on the currency peg, while enabling users to exit, but rewarding users that wait for a transitory downturn to pass.

Importantly, even if stablecoin holders decide to exit, Gyroscope provides _**rational reasons to bet on the stablecoin returning to its target price**_, as the redemption price autonomously recovers back toward peg as outflows equilibrate back toward zero or the reserve recovers (e.g., through yield).

The PAMM design is fully specified, formally characterized, and optimized in our [PAMM technical paper](https://github.com/gyrostable/technical-papers/blob/main/P-AMM/P-AMM%20technical%20paper.pdf).
