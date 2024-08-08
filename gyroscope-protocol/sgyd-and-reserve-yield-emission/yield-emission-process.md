---
description: Explore the process of GYD token distribution and yield allocation
---

# Yield Emission Process

## Yield Emission Process

Yield is periodically emitted to sGYD holders and GYD liquidity providers in a semi-automatic way. Yield is emitted to the set of venues (being defined as the set consisting of sGYD and the gauges of all supported pools) and can then be claimed by users. Specifically, the process is as follows:

1. An off-chain program observes historical time-weighted GYD holdings across the previous evaluation period (typically one week).
2. An off-chain program also computes the profit (computed daily) that accrued to the GYD reserve across the same time frame.
3. Based on these values as well as configured weights and safety parameters (see below), the GYD emissions to all venues are computed.
4. An on-chain contract (the GydDistributor) mints new GYD and distributes them to the different venues. The new GYD remain backed by the surplus value of the reserve.
   * For sGYD, the GydDistributor adds a stream (see below) that emits the GYD across a predetermined emission time window (typically one week). sGYD will emit these GYD by continuously increasing its exchange rate within the time window by a factor that reflects the emitted GYD amount.
   * For pools, the GYD are deposited into the respective pool gauge and are distributed across the following week.

The process runs periodically, typically once per week.\
Note that the yield earned per GYD per day in the different venues need not be equal to the yield that the GYD reserve accrued across the same time frame (see the Risks section below).

## Yield Distribution Formulas

For the exact formulas and code that govern the distribution of yield to venues, see the [Reserve Yield Emission Scripts repository](https://github.com/gyrostable/reserve-yield-emission-scripts).

The following briefly describes these formulas:

1. The reserve profit is computed using a Dune query that computes (1) GYD outstanding and (2) holdings of the GYD reserve and their value on a daily basis. Excess reserve is the difference between items (2) and (1). Reserve profit is the difference in excess reserve across the evaluation time frame.
2. A share of the reserve profit (profit\_share config key, currently 90%) is distributed to venues, while the rest (currently 10%) is retained by the reserve.
3. This amount is distributed across the different venues according to the following weighting rules:
   * By default, distribution is according to the ratio of time-weighted average GYD holdings for each venue.
   * However, distributions are limited by a cap on APR. APR here relates to the average APR per unit of GYD held in the venues over time across the evaluation period:
   * The union of all sGYD deployments is limited to sgyd\_max\_apr (currently 20%).
   * The union of all pools is limited to pools\_max\_apr (currently 4%).
   * If only one of these APR caps is tight, the other group of venues may achieve a higher APR because of this.
   * If both APR caps are tight, fewer GYD are emitted that would be without the APR cap; the un-emitted value is retained by the reserve.
