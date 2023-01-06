---
description: Concentrating liquidity within price bounds defined by the DSM
---

# GYD Trading Pools

## Overview

In Gyroscope, the GYD Trading Pools concentrate the liquidity within a band that follows the minting and redemption quotes set by the DSM.

With healthy reserves, GYD Trading Pools liquidity is concentrated within a narrow band. If there is a shock to the reserve and the DSM sets new redemption prices (as described here) this price band will widen. Notably, the _**GYD Trading Pool**_ _**liquidity provision is very resilient, as:**_

* GYD Trading Pools are _**redundant**_** ** (i.e., provide different paths in/out of GYD) and
* GYD Trading Pools are _**independent**_ from each other (e.g. if the paired asset fails, remaining SAMM pools can still function, unlike one common Curve pool).

### Stylized GYD Trading Pool redemption curve

The stylized GYD Trading Pool redemption curve is shown below against the example of a 50-50 Uniswap pool.

<figure><img src="../../../.gitbook/assets/Graph 1 v3 (1).png" alt="Stylized GYD Trading Pool redemption curve"><figcaption><p>Stylized GYD Trading Pool redemption curve</p></figcaption></figure>

GYD Trading Pool designs incorporate optimized bonding curve shapes and virtual reserve mechanisms. These are fully specified, formally characterized, and optimized in [several papers available on Github](https://github.com/gyrostable/technical-papers/tree/main/E-CLP).&#x20;
