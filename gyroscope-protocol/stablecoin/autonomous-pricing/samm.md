---
description: Concentrating liquidity within price bounds defined by the DSM
---

# Gyro Money Markets

## Overview

In Gyroscope, the Gyro Money Markets concentrate the liquidity within a band that follows the minting and redemption quotes set by the DSM.

With healthy reserves, Gyro Money Market liquidity is concentrated within a narrow band. If there is a shock to the reserve and the DSM sets new redemption prices (as described here) this price band will widen. Notably, the _**Gyro Money Market liquidity provision is very resilient, as:**_

* Gyro Money Markets are _**redundant**_** ** (i.e., provide different paths in/out of GYD) and
* Gyro Money Markets are _**independent**_ from each other (e.g. if the paired asset fails, remaining SAMM pools can still function, unlike one common Curve pool).

### Stylized Gyro Money Market redemption curve

The stylized Gyro Money Market redemption curve is shown below against the example of a 50-50 Uniswap pool.

<figure><img src="../../../.gitbook/assets/Graph 1 v2.png" alt=""><figcaption></figcaption></figure>

Gyro Money Market designs incorporate optimized bonding curve shapes and virtual reserve mechanisms. These are fully specified, formally characterized, and optimized in [several papers available on Github](https://github.com/gyrostable/technical-papers/tree/main/E-CLP).&#x20;
