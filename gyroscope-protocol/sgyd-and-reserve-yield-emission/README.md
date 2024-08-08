---
description: An Overview of sGYD (savings GYD) and Yield Emission
---

# sGYD and Reserve Yield Emission

_DISCLAIMER:_&#x20;

_The information provided below regarding sGYD and Reserve Yield Emission is for informational purposes only and should not be considered financial advice. Users should conduct thorough research and consult with a financial, legal and technical advisor before interacting with sGYD. It is the responsibility of each participant to understand the risks of sGYD and to comply with all applicable laws and regulations in their jurisdiction. sGYD is not available in the United States, United Kingdom and selected other jurisdictions. See the_ [_Terms of Service_](https://gyro.finance/terms-of-service) _for more information._

The reserve backing the GYD stablecoin earns yield on its underlying assets. Since GYD and the Gyroscope Protocol are decentralized, that yield remains in the protocol. The Protocol was designed in a way that the majority of this yield can be emitted to users who have staked GYD in two categories of venues: (1) GYD’s yield-bearing token sGYD and (2) certain liquidity pools where GYD is traded against another asset. Reserve yield is emitted in the form of newly minted GYD.

## Earning Reserve Yield through sGYD

sGYD is the yield-bearing version of the GYD stablecoin, following a standard yield-bearing vault design (ERC4626). This means that GYD can be deposited into / withdrawn from sGYD at any time and earns yield while it is deposited in sGYD. sGYD is not rebasing; instead, the deposit/withdrawal exchange rate increases automatically over time to reflect the yield emitted to sGYD holders. sGYD is transferable in a permissionless way.

Users can interact with sGYD either directly on-chain through the ERC4626 functions or through a frontend like the UI hosted on gyro.finance, subject to the applicable restrictions and Terms of Service (see the disclaimer above).

See below for details on how exactly the sGYD yield is computed and emitted.

## Earning Reserve Yield when LPing in GYD pools

Liquidity providers who hold shares of an AMM pool containing GYD can earn reserve yield on the GYD portion of their corresponding holdings. To do this, they deposit their LP shares into the corresponding Balancer gauge. This can be done directly on-chain or through any frontend that supports it, such as [the UI](https://app.gyro.finance/pools/ethereum/) hosted on gyro.finance or [the UI](https://balancer.fi/pools) hosted on balancer.fi. For supported pools, GYD then accrues as a reward token, analogous to BAL rewards. Rewards can be claimed at any time.

Only some GYD pools are eligible to participate in such reserve yield emissions (see “Supported Venues” below). The set of eligible pools is determined by protocol governance.\


See below for details on how exactly the yield to pools is computed and emitted.

{% content-ref url="yield-emission-process.md" %}
[yield-emission-process.md](yield-emission-process.md)
{% endcontent-ref %}

{% content-ref url="security.md" %}
[security.md](security.md)
{% endcontent-ref %}

{% content-ref url="code-repositories-and-audits.md" %}
[code-repositories-and-audits.md](code-repositories-and-audits.md)
{% endcontent-ref %}

{% content-ref url="sgyd-internals.md" %}
[sgyd-internals.md](sgyd-internals.md)
{% endcontent-ref %}
