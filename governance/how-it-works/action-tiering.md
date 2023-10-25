# Action Tiering

Some actions taken by governance are much more impactful and riskier than others.

To reflect these different levels of importance, every function that can be called through governance is assigned a tier. At the moment, the tiers implemented are:

<table><thead><tr><th width="231">Tier</th><th>Description</th></tr></thead><tbody><tr><td>LOW</td><td>Small governance spending, fine-tuning</td></tr><tr><td>MEDIUM</td><td>Changes to parameters / system components that could have indirect safety implications</td></tr><tr><td>HIGH</td><td>Changes to parameters / system components that can have direct safety implications</td></tr><tr><td>CORE</td><td>Changes to the entire system / essentially upgrades</td></tr><tr><td>HIGH-TREASURY</td><td>Like HIGH but is not disabled when upgrades are disabled. For large treasury spending</td></tr></tbody></table>

A tier contains the following information:

* `proposalThreshold`: the minimum voting power required to create a proposal
* `quorum`: the quorum to be reached for the proposal to pass
* `voteThreshold`: the minimum ratio of `for` votes for the vote to pass
* `timeLockDuration`: the length of the time lock
* `proposalLength`: the length of the proposal
* `actionLevel`: how "impactful" the given action is

Assigning a tier is done using an `ITierStrategy` implementation and varies depending on the function called.

The following strategies are implemented:

* `StaticTierStrategy`: always returns the same tier regardless of the arguments
* `SimpleThresholdStrategy`: returns a tier based on whether one of the parameters is above a given threshold
* `SetVaultFeesStrategy`: Same as `SimpleThresholdStrategy` but compares two arguments to the threshold
* `SetSystemParamsStrategy`: Similar to `SimpleThresholdStrategy` but compares a several fields of a `struct` to multiple thresholds
* `SetAddressStrategy`: Has a different tier per address argument. This is used for the `GyroConfig.setAddress` that has the power to replace parts of the system.
