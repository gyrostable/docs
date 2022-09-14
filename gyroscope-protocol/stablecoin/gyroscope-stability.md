---
description: Additional mechanisms that complement primary stability mechanisms
---

# Complementary stability mechanisms

## Complementary stability mechanisms <a href="#a8bb" id="a8bb"></a>

Gyroscope also incorporates several complementary stability mechanisms, which work together with the core Gyroscope mechanisms to strengthen stability.

### Integration with Leveraged Loans

Akin to Maker’s Peg Stability Module (PSM), the core Gyroscope mechanism allows exchangeability of the stablecoin with ˜1$ worth of assets. However, unlike Maker’s design it does so while (1) allowing to diversify all risks in the reserve, (2) not entirely relying on custodial stablecoins, and (3) preserving some resilience and flexibility to survive even if the reserve value fluctuates.

The leveraged loan mechanism may thus provide another way in which Gyroscope participants can rationally support the peg if the reserve becomes under-collateralized. In particular, if the GYD price ever falls significantly below $1 (e.g., if there is a significant cryptocurrency crash), then leverage holders will be able to deleverage their positions at a discount. This has the further effect of reducing the GYD supply and returning the GYD price toward $1.

### Recapitalizing Actions

The reserve can be recapitalized through auctioning governance tokens or future reserve yields. Governance is incentivized to do this at opportune times as opposed to solely as last resorts in the middle of a crisis. If times are good, and governance token valuation is sky high, governors are incentivized to auction off new tokens early to boost the reserve. See _reserve securitization_ in the [white paper](https://gyro.finance/pdfs/Gyroscope\_Lite\_Paper.pdf).

More coming soon.&#x20;
