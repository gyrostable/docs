# Gyroscope governance 

The Gyroscope governance system is designed to bring many different stakeholder groups into governance.
Voting power is split between a number of different voting vaults, which allocate voting power to different stakeholder groups.
Furthermore, the quorum, time delay, and other parameters are set depending on the impact of the proposed changes.

# Voting power computation

The voting power of a user is computed by the `VotingPowerAggregator` contract.
This contract loops over all the vaults of the system and sums up the voting power of the user in each vault weighted with the vault's weight.
Each vote has different rules for how voting power is computed.
In most vaults, the voting power can be delegated, which decreases the voting power of the account delegating and increases the voting power of the one delegated.

The following vaults are currently implemented:

1. `FoundingFrogVault`: Every owner of a Gyro founding frog (NFT distributed on Ethereum) starts with a prescribed voting power. To claim the voting power, a user must submit a Merkle proof that it owns a founding frog by signing a message. The Merkle proof is generated from a snapshot of founding frog holders. Governance can later decide to increase the voting power of some users by calling `NFTVault.updateMultiplier`
2. `RecruitNFTVault`: This vault is similar to the `FoundingFrogVault` but the voting power is assigned when minting a `RecruitNFT`
3. `FriendlyDAOVault`: This vault allows governance to arbitrarily assign voting power to any address by calling `FriendlyDAOVault.updateDAOAndTotalWeight`. In practice, this will be used to give voting power to other DAOs that are part of the Gyroscope ecosystem.
4. Locking vaults: The `LPVault` allows a user to lock a given token (such as LP tokens or GYFI) to earn voting power. There can be as many `LPVault` in existence as we decide to support different tokens. An locking vault for LP assets could be incentivised through a liquidity mining scheme implemented in its parent `LiquidityMining` contract
5. `AggregateLPVault`: This aggregates the voting power across a set of registered `LPVault`s (e.g., all vaults that lock are set up for LP shares). The `LPVault`s are weighted through governance.

The weights of different voting vaults should sum to 1 (representing 100% of total voting power) and change over time according to a schedule set in `VotingPowerAggregator`. A schedule starts from initial weights at the starting time and arrives at final weights at the ending time with weights changing linearly over time. A new schedule can be set by governance by calling `VotingPowerAggregator.setSchedule`.

# Action tiering

Every function that can be called through governance is assigned a tier.
A tier contains the following information:

- `proposalThreshold`: the minimum voting power required to create a proposal
- `quorum`: the quorum to be reached for the proposal to pass
- `voteThreshold`: the minimum ratio of `for` votes for the vote to pass
- `timeLockDuration`: the length of the time lock
- `proposalLength`: the length of the proposal
- `actionLevel`: how "impactful" the given action is

Assigning a tier is done using an `ITierStrategy` implementation and varies depending on the function called.

The following strategies are implemented:

- `StaticTierStrategy`: always returns the same tier regardless of the arguments
- `SimpleThresholdStrategy`: returns a tier based on whether one of the parameters is above a given threshold
- `SetVaultFeesStrategy`: Same as `SimpleThresholdStrategy` but compares two arguments to the threshold
- `SetSystemParamsStrategy`: Similar to `SimpleThresholdStrategy` but compares a several fields of a `struct` to multiple thresholds
- `SetAddressStrategy`: Has a different tier per address argument. This is used for the `GyroConfig.setAddress` that has the power to replace parts of the system. 


# Proposal lifecycle

1. Proposal creation: A proposal, which is a list of calls to execute, is created by a participant using `GovernanceManager.createProposal`
    1. The tier (containing quorum and other metadata, see `DataTypes.Tier`) is set to the highest tier of any of the calls to execute
    2. The proposer votes are computed and checked against the proposal threshold (part of the tier information)
    3. If the proposer has enough voting power, the proposal is started
2. Voting phase
   1. Any participant with voting power is allowed to vote "for", "against", or "abstain" using `GovernanceManager.vote`
   2. A participant can change his vote at any time
3. Proposal conclusion: a vote can be concluded by anyone using `GovernanceManager.tallyVote`
   1. If the quorum is reached and the vote threshold is reached, the proposal is queued for execution
   2. If not, the proposal is marked as rejected
4. Proposal execution: a proposal can be executed by anyone using `GovernanceManager.executeProposal` once the time lock for the tallied proposal has passed


# Emergency recovery

An emergency recovery mechanism for the governance contract is included as a fallback in case something goes wrong with the governance contracts and they are no longer usable (e.g, if they are bricked because of a smart contract bug or incorrect parameterization change). The emergency recovery mechanism is composed of a backup multisig combined with an optimistic approval mechanism and various safeguards as implemented in `EmergencyRecovery`.

The emergency recovery mechanism has the following properties:
- Multisig signers are assigned by governance and can be changed at any time
- The multisig can initiate an upgrade to the governance contract subject to a timelock
- (Optimistic approval) during the timelock, governance can vote to override the upgrade
- Emergency recovery has a sunset built in, which can optionally be extended by governance


# Governance checks and balances

On top of the basic voting structure, the governance system includes several checks and balances and safety mechanisms.

### Power of GYD users to limit upgradeability

A special form of optimistic approval is used to give end users of the protocol (GYD stablecoin holders) power over governance regarding how upgradeable the protocol should be. This takes the form of an alternative 'wrapped' form of GYD that can affect governance settings.

As implemented in `WrappedERC20WithEMA`, at any time, a user can choose between holding GYD or the wrapped wGYD and can freely convert between them. Choosing to hold wGYD signifies a vote for more limited upgradeability of the protocol. When a user converts between GYD and wGYD, a moving average is updated in the wGYD contract. When the moving average exceeds a threshold in addition to the total wGYD supply exceeding another threshold, upgradeability of core Gyroscope contracts through governance becomes more difficult. This takes the form of increased difficulty in action tiering.

The main idea is to let the user market decide when the system should be more upgradeable and when core infrastructure should be considered more settled based on the market choice of whether to adopt GYD or wGYD.

#### Tracking the Moving Average

We track the moving average of the share of wGYD to GYD in terms of an irregularly-spaced exponential moving average (EMA) as follows. Index the points in time where the EMA is updated by $i$, where $i=0$ marks deployment of the contract. Let $t_i$ be the block height at time index i, and let $x_i := \text{wGYD supply}/\text{GYD supply}$ at the end of block $t_i$. Let $y_i$ be the EMA at time index $i$. We can define the EMA as

$$
\begin{align*}
y_0 &= 0
\\
y_{i} &= y_{i-1} + K_i \cdot (x_i - y_{i-1}) \quad\text{if $i > 0$}
\\
\text{where } K_i &= 1 - e^{-(t_{i} - t_{i-1}) / \tau}.
\end{align*}
$$

Here, $\tau$ is a constant (i.e., a parameter to the contract) that is usually interpreted as the width of a time window. Observe that, if the spacing of the $x_i$ time series was regular, then all the $K_i$ would be equal, but in our case, this does not hold. The definition of $K_i$ is motivated by the continuous form of the EMA from signal processing, see [here](https://stackoverflow.com/a/1027808/266614).

Note that we only track the EMA at the *previously updated block*, not the current block. This is to prevent manipulation of the EMA by, e.g., using a flash loan. The values $x_i$ and $t_i$ in the above formulas therefore refer to the most recently-observed values that are not from the current block; the current-block values are not used to update the current-block EMA, but will only be used in the next block.

The variables in `_updateEMA()` match the variables from the formulas above as follows:

| Math      | Code                                 |
|-----------|--------------------------------------|
| $y_{i-1}$ | `expMovingAverage.value`             |
| $x_i$     | `previousWrappedPctOfSupply.value`   |
| $t_{i-1}$ | `expMovingAverage.blockNb`           |
| $t_i$     | `previousWrappedPctOfSupply.blockNb` |
| $\tau$    | `windowWidth`                        |
### Reserve stewardship incentives

An important ability of governance is to be a good steward of the GYD reserve structure, adapting it as the DeFi space changes. This requires safeguards against governance misincentives. This mechanism imposes conditions on cash flows being realized by governance to help keep incentives of governance aligned with the best interest of the longterm system.

This mechanism is implemented in `ReserveStewardshipIncentives` in the `Protocol` repository as it requires integration with the protocol code.

Governance can initiate an incentive initiative by calling `startInitiative`. To start an initiative, it is required that the system has excessive health properties (e.g., that the reserve ratio is above an excess threshold). Specifying an initiative includes specifying a `rewardPercentage`.

Once an initiative is active, several health properties of the system are tracked over a long period of time, as performed via `_checkpoint`. This includes tracking the average GYD supply and the number of days that reserve health violations are observed over this time period.

At the end of the time period, governance can call `completeInitiative`, which verifies whether health properties were achieved over the term of the initiative and, if so, calculates an incentive reward based on `rewardPercentage` and the average GYD supply over the term. The size of the reward is limited by a condition on the health of the system that would follow any reward. If `rewardPercentage` is too high considering the end health of the system, the reward calculation also imposes a penalty, reducing the size of the end reward.

The end result is intended to be a structure in which incentive rewards are only given to governance after their stewardship has proven successful over a long time period.

### GYD recovery module

This module is a tool available to governance to incentivize a backstop to the protocol. It is implemented in `GydRecovery` in the `Protocol` repository as it requires integration with the protocol code.

Any user can deposit GYD to the recovery module to backstop the system. A user can initiate a withdrawal of their staked GYD subject to an unstaking period. The contract tracks an adjusted form of balances that accounts for any recovery operations that are performed.

If the reserve ratio falls below a trigger ratio, a burn of GYD in the recovery module is performed. The amount of the burn is the amount, if possible, to bring the system back to a target reserve ratio. A partial burn is when not all GYD in the module is burned and is performed by modifying the `adjustmentFactor` affecting adjusted balances. A full burn is when all GYD in the module is burned and is handled separately.

The GYD recovery module is set up with liquidity mining infrastructure. Governance can choose to allocate incentive assets in the form of GYFI tokens to the recovery module and can start or stop the mining of these incentives by participants who have staked GYD in the module.