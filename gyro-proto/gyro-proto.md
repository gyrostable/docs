---
description: Gyro Proto is a beta version of the Gyroscope stablecoin system.
---

# Gyro Proto

## Where can I try it?

Try out Gyro Proto [here](https://app.gyro.finance/dsm/).&#x20;

## Gyro Proto Implementation

Gyro Proto (p-GYD) is a beta version of the Gyroscope stablecoin system. It is released in a guarded form on Polygon for testing purposes prior to the full Gyroscope launch on Ethereum.

After Q1 ’23, the proto system will continue as a platform for testing future protocol updates. Users may continue to use the proto-system, but will be encouraged to remove committed assets before the final protocol launch on Ethereum.&#x20;

<figure><img src="https://lh4.googleusercontent.com/BksD8MLIr3jc5GkDDekDOzJiUtsZ0ocyW4NUTLlxAmnqAmkVndu_pzM4gxcOV3NkzCT2NNcdM72CHEt3xAbPhraPPg4gT8eHH-ztKhWIeMrdbpzvexePgG2NCD_bLXDgszUE6JAfLlkzWuG6E2wnbBHwZAvNLEECkrI2dmwHkeeRgR9Lu4IT7EOO1-vKVg" alt=""><figcaption><p>Comparing Gyro Proto to the final Gyroscope protocol</p></figcaption></figure>

## Aims of Gyro Proto

The aim of the Gyro Proto release is to test the protocol in a live setting: in particular, the smart contracts and their interactions in a production environment. Following a testing period, the goal is to hand over well-calibrated and tested contract code to Gyroscope governance so that it can launch the final system at its discretion.

Considering that the aim is code testing alone over a limited period of time, Gyro Proto is calibrated for simplicity and ease of use on Polygon. This means that it is purposefully not calibrated for important aims like long-term economic resilience and is not necessarily representative of how the full system should be calibrated.

One place to highlight in the calibration of Gyro Proto is the selection of reserve assets. A simple reserve structure was chosen considering the following:

1. The limited selection of assets on Polygon with reasonable liquidity
2. The desire to test 2-CLP, 3-CLP, and E-CLP liquidity pools within the reserve
3. The desire to test the system in a range of reserve ratio states

The Gyro Proto reserve is thus initialized with simple 2-CLP, 3-CLP, and E-CLP pools composed of other stablecoins. Most of these pools were previously launched for CLP testing purposes. The selection of reserve assets for the final system will be subject to approval by Gyroscope governance.

A small proportion of WETH is also enabled in the reserve. The reason for this is so that the reserve ratio will fluctuate in the short-term, allowing system functionality to be tested in a wider range of settings. While in the long-term, the price of stablecoins in the reserve may deviate from 1 USD, this is unlikely in the short-term, and thus the inclusion of WETH allows the code to be tested under different reserve ratio scenarios.

## Asset caps

Gyro Proto is a guarded system with asset caps to contain risk. Individual addresses are limited to contributing a nominal amount of assets (10 USD) for testing purposes. Users may be able to get on a guarded whitelist for a higher asset cap, but this is not recommended for most users and there is no envisioned benefit to doing so. Gyro Proto also has a total asset cap of 100k USD.

## Upgradeability of Gyro Proto contracts

In Gyro Proto, smart contracts are being tested in a real environment for the first time.While the contracts have been audited, the risk of code bugs cannot be fully mitigated.  As such, it is important that both the community and the development team at FTL Labs, who is [mandated](https://snapshot.org/#/gyrodao.eth/proposal/QmeMYwoCCEhSk8E7BNshU2XeSD91RVdLrkkv3mSV2EApTe) to deliver v1 of the protocol, are able to quickly address smart contract issues that may be found. For this reason, FTL Labs will temporarily retain control over the proto-system parameters and protocol update and design decisions.

Following the Gyroscope governance launch, updates to Gyroscope contracts will have to be enacted by Gyroscope governance. This is fundamentally important to launching Gyroscope as a decentralised protocol.

## Risks of using Gyro Proto

Using Gyro Proto also comes with certain risks, including the following.

* **Smart contract risk**: As with any smart contract system, there is an inherent risk that an exploit or bug puts committed assets at risk. This risk can be reduced by conducting code audits and testing, but it cannot be fully mitigated.
* **Risks of reserve assets:** The Gyroscope system is backed by reserve assets, which may include other stablecoins, LP shares in AMM pools, and other tokens. Each of these assets has its own risks, and there is no guarantee that Gyroscope reserve assets always have enough value to fully back the system. More information on stablecoin risks is described, for example, in [this paper](https://arxiv.org/abs/2006.12388). Further, since these assets are on the Polygon blockchain, they may also carry risk of the bridge carrying them over from other chains. More information on LP risks is described in the CLP docs. While these asset risks have been studied (like in the provided links), cryptocurrencies remains a new space in which risks may not be fully understood yet. As described above, Gyro Proto incorporates WETH as a reserve asset, and participating in Gyro Proto involves some ETH exposure risk. Due to the volatility of ETH, the system may be expected to become under-reserved at times during testing.
* **Price oracle risks**: The Gyroscope system relies on a system of price oracles to import asset pricing information from off-chain markets and to read pricing information from on-chain markets. At times, these oracles may provide wrong information or may be manipulated, which may lead to system losses on reserve assets. Oracle risks are described further, for example, in [this paper](https://arxiv.org/abs/2006.12388) and in the [oracle system specification](https://github.com/gyrostable/technical-papers/blob/main/Consolidated%20Price%20Feed%20and%20Circuit%20Breakers/Design%20of%20the%20Consolidated%20Price%20Feed%20and%20Circuit%20Breaker%20System.pdf). While the Gyroscope design attempts to mitigate oracle risks, some residual risk always remains.
* **Risks of using the DSM**: The DSM defines the system’s monetary policy of how reserve assets are used toward maintaining a stablecoin peg. The DSM is designed to balance maintaining a peg with preserving reserve assets in the scenario that reserve assets experience shocks and the system becomes under-reserved. By the design of the DSM (and transparent on-chain), there is no guarantee that users are able to redeem GYD from the system at a value near the peg price at all times. In addition to drawdown risk due to volatility of reserve assets, the DSM may lead to additional drawdown of reserve value. The DSM monetary policy is designed to allow some level of redemptions near the stablecoin peg while the system is under-reserved, which would draw down the overall reserve ratio available for later redemption. This additional drawdown depends on the level of inflows and outflows that the system experiences while under-reserved and on the calibration of the DSM. The DSM is designed to be bounded by a DSM parameter, as described in the [DSM technical paper](https://github.com/gyrostable/technical-papers/blob/main/P-AMM/P-AMM%20technical%20paper.pdf).
* **Upgradeability risk**: The Gyro Proto contracts are upgradeable, meaning that the smart contract code may change over time. While it is intended that smart contract upgrades for Gyro Proto would fix any code bugs that may materialize, upgrades may also introduce new vulnerabilities and have their own smart contract risk.
* **Blockchain infrastructure risk**: As the Gyro Proto contracts are deployed on the Polygon PoS blockchain, any interaction with the smart contracts inherits the risks of the Polygon PoS blockchain.
* **UI and blockchain interaction risks**: When a user interacts with the Gyro Proto system through the Gyro Proto web UI, they are exposed to technical risks. While the Gyro Proto UI has been carefully reviewed to avoid bugs and vulnerabilities, these cannot be completely excluded. A UI bug may lead to an incorrect transaction being generated, or the UI may become unavailable. A user’s own IT setups (e.g. web browser, wallet software) may further contain bugs and vulnerabilities.

Any of the above risks can lead to a partial or complete loss of the user’s assets.
