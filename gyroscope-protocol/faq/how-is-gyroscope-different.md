---
description: Differentiating Gyro from other stablecoins
---

# How is Gyroscope different?

Gyro is designed to be DeFi's all-weather currency. Gyro is designed to uniquely address the following major challenges for non-custodial stablecoins.

1. **Scalability**: the ability to meet high levels of demand in a sustainable way. While we like over-collateralized stablecoins like Dai, they rely on the leverage-long ETH market to scale, which has run into issues and likely will again.
2. **Safe during crashes**: the ability to maintain a peg within a tight band during market turbulence without invoking trust assumptions (e.g., tethering to USDC);
3. **Aligned governance**: having a governance mechanism that incentivizes the long-term health of the stablecoin, rather than short-term profit.

We expand on these ideas in a three part series: [Part I](https://medium.com/gyroscope-protocol/gyroscope-is-different-part-1-72dcb8c303a4), [Part II](https://medium.com/gyroscope-protocol/gyroscope-is-different-part-2-algorithmic-stablecoins-78c53c005e89),  Part III (coming soon).

| In comparison to                         | Gyroscope's design improvement                                                                                                                         |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Meta-Stablecoins                         | Better risk segregation: [Part I](https://medium.com/gyroscope-protocol/gyroscope-is-different-part-1-72dcb8c303a4)                                    |
| Algorithmic stablecoins                  | Resilience over confidence crises: [Part II](https://medium.com/gyroscope-protocol/gyroscope-is-different-part-2-algorithmic-stablecoins-78c53c005e89) |
| Custodial and leverage based stablecoins | Part III (coming soon)                                                                                                                                 |

## **Meta-Stablecoins** <a href="#e55d" id="e55d"></a>

Meta-stablecoins are stablecoins that are composed of a basket of other stablecoins. The idea is that the basket diversifies the risks of the individual stablecoins. This can create a new type of risk for the stablecoin, called composability risk: the risk that a problem in one system can cascade into other systems. For more discussion, see our [article here](https://medium.com/gyroscope-protocol/gyroscope-is-different-part-1-72dcb8c303a4). **** Gyroscope’s all-weather reserve is designed to be resistant to these composability risks.

## Algorithmic Stablecoins

Algorithmic stablecoins aim to maintain a stable price by automatically adapting the stablecoin supply to meet demand. Algorithmic stablecoins up until this point have tried to address the scalability challenge in a flawed way: by trying to produce as many stablecoins for as little collateral as possible. For instance, the Basis type designs try to maintain stablecoins with no collateral. These and related seigniorage shares designs, based on "endogenous collateral", rely on a sense of self-fulfilling expectations about the system or its future cashflows. However, these cashflows are very fragile and can disappear in a crisis. Other newer attempts lie somewhere in between these types of designs and full reserve designs.

This is flawed because it is unnecessary for scalability and can come at the expense of the system. To see why, consider that in any functioning stablecoin, someone always buys newly minted stablecoins for $1. A key question is where this $1 goes. In under-collateralized designs today, much of this is paid out to protocol stakeholders at the expense of system health.

Gyroscope is not like those algorithmic stablecoins. Instead, all of every $1 paid for a new stablecoin goes into a reserve that aims to be 100% reserved. This is as scalable as other algorithmic designs, it just diverts the seigniorage revenue to the right places.

For further discussion of how Gyroscope compares to algorithmic stablecoins, including resistance to bank runs, read our [article here](https://medium.com/gyroscope-protocol/gyroscope-is-different-part-2-algorithmic-stablecoins-78c53c005e89).

![](<../../.gitbook/assets/Algorithmic Stablecoins Confidence Crisis Flow Chart.png>)

## Custodial and Leverage-based Stablecoins

Coming soon. Read ahead in our [Stablecoins 2.0](https://arxiv.org/abs/2006.12388) paper
