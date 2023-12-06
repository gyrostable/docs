---
description: A non-technical overview of Gyroscope
---

# tldr: What is Gyroscope

Gyroscope is a decentralized stablecoin featuring a novel all-weather stablecoin design combined with more efficient stablecoin liquidity pools.

## Gyro Dollars

Gyroscope’s stablecoin Gyro Dollars (GYD) is designed to be fully backed by a basket of assets with fundamental innovations in risk control built in at the protocol level. GYD’s innovations aim to segment and contain risks from across the asset space and include:

* Automated risk diversification rules,
* Optimized minting and redemption bonding curves that guide the protocol on how to use reserve assets to maintain stability,
* A new resilient oracle and circuit breaker system that handles stress.

GYD is designed to protect against the main risks of holding stablecoins, placing risk control at a high degree of automation in a decentralized, non-custodial way. It serves as a principled risk control layer for stablecoin holders. GYD, which aims to form the safest on-chain stable asset, implements these design principles.

## E-CLPs

Gyroscope E-CLPs, standing for elliptic concentrated liquidity pools, are a novel liquidity pool type that enables asymmetric concentration of liquidity. E-CLPs focalize trading of assets along the curve of an ellipse.

E-CLPs have several advantages over other liquidity pool types:

* E-CLPs are up to 75% more efficient than Stableswap liquidity pools. They greatly improve capital efficiency for liquidity providers (LPs).
* E-CLPs are highly customizable. They allow a further degree of flexibility as liquidity no longer needs to be spread evenly within uniform price bounds.
* E-CLPs don’t require active position management and adapt automatically to yield-accruing assets. The pool deployer takes on responsibility of calibrating and establishing trading parameters upon launch.

E-CLPs package concentrated liquidity into a customizable and passive form.

## GYD and E-CLPs

GYD and E-CLPs are complementary. While E-CLPs have use cases outside of GYD, they also integrate closely together.

GYD and E-CLPs together aim to achieve:

* Enhanced stability for GYD: optimized E-CLP trading pools for GYD provide more liquidity at the prices that matter around the peg price. This is backed up by support from the protocol’s mint and redemption mechanism.
* A more efficient collateral class of LP shares for backing GYD. E-CLPs are used as a yield strategy for reserve assets.

Longer term, LP positions in LST E-CLPs could be integrated into a leverage mechanism for GYD. This would allow GYD to be borrowed against the highly efficient yield-bearing collateral type arising from E-CLPs.

Lastly, GYD is launched with a special ‘bootstrapping E-CLP’, implemented at the protocol level, which provides an initial simplified way to acquire GYD. The bootstrapping pool provides a pre-set amount of GYD that can be ‘minted’ against sDAI as a reserve asset by swapping through the pool. This is provided as a more straightforward alternative to minting directly against reserve assets, which is a complex process expected to be undertaken by sophisticated market makers in the future. sDAI reserves from the bootstrapping pool will later be unwound into the wider Gyroscope reserve.

\
