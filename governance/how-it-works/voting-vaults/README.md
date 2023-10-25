# Voting Vaults

## Why are there voting vaults?

Pluralism is the view that power should be dispersed among a variety of centres of power, and not held by a single group. The assumption is that diversity of governing voices is beneficial to a protocol.

Voting vaults are a structure that enable a pluralist approach. The hope is that having a variety of voices involved in the governance of the protocol results in effective long term stewardship of it.

At present, many on-chain governance systems rely solely on a governance token to effect their on-chain governance. Such systems do not ensure pluralism by design because ownership of governance tokens alone results in voting power.&#x20;

## What sorts of vault are there?

The following vaults are currently implemented:

1. [The Founding Member Vault](the-founding-member-vault.md): every owner of a Gyro founding frog (an NFT distributed on Ethereum) can claim some voting power
2. [Councillor Vault](councillor-vault.md): selected Councillors who have minted a Councillor NFT (distinct from the Founding Frog NFT) can claim voting power
3. [Associated DAO Vault](associated-dao-vault.md): this vault allows governance to assign voting power to other DAOs that are part of the Gyroscope ecosystem.
4. [GYFI Vault](gyfi-vault.md): this vault allows a user to lock GYFI tokens to earn voting power.&#x20;
5. [GYD LP Vault](gyd-lp-vault.md): this vault aggregates the voting power across a set of pools in which the user is providing GYD liquidity.

## How is voting power computed?

The voting power of a user is computed by the `VotingPowerAggregator` contract. This contract takes the total voting power of each address in each vault and weights this by the voting weight of each vault.&#x20;

Each vault has different rules for how voting power is computed. In most vaults, the voting power can be delegated, which decreases the voting power of the account delegating and increases the voting power of the one delegated.

Together, the weights of the voting vaults sum to 1 (representing 100% of total voting power). These weights can change over time according to a schedule set in `VotingPowerAggregator`. A schedule starts from initial weights at the starting time and arrives at final weights at the ending time with weights changing linearly over time. A new schedule can be set by governance by calling `VotingPowerAggregator.setSchedule`.

##
