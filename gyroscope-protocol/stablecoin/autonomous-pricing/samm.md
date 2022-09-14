---
description: Concentrating liquidity within price bounds defined by the PAMM
---

# Secondary-market AMM

## Overview

In Gyroscope, the secondary market AMM concentrates the liquidity within a band that follows the minting and redemption quotes set by the primary market AMM.

With healthy reserves, SAMM liquidity is concentrated within a narrow band. If there is a shock to the reserve and the PAMM sets new redemption prices (as described here) this price band will widen. Notably, the _**SAMM liquidity provision is very resilient, as:**_

* SAMMs are _**redundant**_** ** (i.e., provide different paths in/out of GYD) and
* SAMMs are _**independent**_ from each other (e.g. if the paired asset fails, remaining SAMM pools can still function, unlike one common Curve pool).

### Stylized SAMM redemption curve

The stylized SAMM redemption curve is shown below against the example of a 50-50 Uniswap pool.

![](../../../.gitbook/assets/Stylized\_SAMM\_Redemption\_Curve\_v4.png)

SAMM designs incorporate optimized bonding curve shapes and virtual reserve mechanisms. These are fully specified, formally characterized, and optimized in our SAMM technical paper, which will be released soon. See the white paper Section 3.5 for some further details.
