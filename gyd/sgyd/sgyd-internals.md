---
description: Explore sGYD’s internal emission and exchange rate mechanisms
---

# sGYD Internals

This section explains some internal operations of sGYD. Most users likely do not need to concern themselves with these details; they can simply interact with sGYD using the ERC4626 interface or the UI. For example, `convertToAssets(1e18)` yields the current sGYD/GYD exchange rate.

Emissions to sGYD are stored in a structure called a stream. A stream consists of the amount to be emitted as well as a start and end timestamp. The respective amount is emitted linearly between the start and end times. The set of active and pending streams can be queried using the `streams()` method. Expired streams are periodically cleaned up.

sGYD always holds the total amount of GYD deposited, both by users and in streams. If there are active streams, some of this amount is considered pending (unemitted). This amount can be queried via the `totalPendingAmount()` method. The ERC4626 method `totalAssets()` returns the total amount that could be withdrawn at that time, which is equal to `GYD.balanceOf(sGYD) - sGYD.totalPendingAmount()`. The exchange rate is then equal to `convertToAssets(ONE) = totalAssets() / totalSupply()` (where all operations should be in 18-decimals fixed point).
