# Protocol fees

The Gyroscope protocol is designed with various protocol fee options that may accrue value to the protocol. These include, protocol fees on CLPs, mint/redeem fees for GYD, and yield accrued from reserve assets.

Where enabled, protocol fees accrue by default as Gyroscope reserve assets (e.g., as extra backing for GYD). The main reserve assets backing GYD take the form of AMOs (algorithmic market operations), which provide AMM pool liquidity for GYD, and DSM reserves, which are redeemable via the DSM. These reserves are intended to always back GYD 1:1 or more. Yield on these reserve assets and mint/redeem fees on GYD accrue automatically to growing these reserve assets. The [conditional cashflows](../governance/how-it-works/conditional-cashflows.md) mechanism provides a route to reward governors for stewarding these reserves with various protections for the protocol.

Protocol fee collection contracts are used to collect protocol fees on CLPs, which form by default another arm of the reserve.

The reserve can spend funds to the extent that it has a surplus with funds possibly going out of the reserve to fund protocol security and growth. Excess reserves can be used for bootstrapping further elements of the protocol, like CLPs, with the LP shares remaining as reserve assets. Excess reserves can also be used as incentives, e.g., for sGYD or incentives on CLPs. This enables a flywheel where new incentives on pools generates more fees to the reserve, which in turn generates more ability to bootstrap new pools.

\
