---
description: Learn how secure measures protect GYD yield distribution processes
---

# Security

The distribution of reserve yield is a security-sensitive process. Because of this, the following security measures are implemented:

1. The off-chain program does not have an ability to trigger the emission of yield on its own. Instead, the off-chain program (represented on-chain by the Distribution Submitter EOA) can only submit a pending distribution to an on-chain intermediate contract (the DistributionManager). With no further action, this submission has no further effect.
2. To emit GYD, the pending distribution has to be confirmed by a distinguished trusted party called the Distribution Executor. The trusted party calls the executeDistribution() method of the DistributionManager with no arguments. The DistributionManager is the only authorized address that can trigger the distribution from the GydDistributor and the GydDistributor is the only address in the system that can mint new GYD.
   * Currently, the trusted party is a multisig controlled by the Gyroscope Foundation.
   * In the future, the trusted party will be part of the decentralized governance system.
3. Pending distributions can be publicly reviewed and are time-locked: at least 5 minutes (see DistributionManager.minExecutionDelay()) need to pass between the submission and the execution of a distribution; otherwise, execution fails. The purpose of this is to allow a protected time window for review and to prevent a well-timed attack in case the submission key becomes compromised.
4. The GydDistributor stores a whitelist of venues to which yield emission is possible. The whitelist can only be changed by governance.
5. Calls to the GydDistributor always happen on Ethereum and new GYD are always minted on Ethereum. To distribute yield to a venue on another chain, the GydDistributor internally handles bridging using Chainlink CCIP. The other end of the bridging process is covered by an L2Distributor contract, which does not have any ability to mint GYD.

The system also implements various sanity checks to protect against yet-unknown attack vectors that might attempt to create excessive emissions. Specifically:

* Each individual distribution can emit at most 1% of the total GYD supply (see GydDistributor.maxRate()).
* At most one distribution can be made every 24 hours to the same venue (see GydDistributor.minimumDistributionInterval())
* For sGYD, streams (see below) cannot have pathological parameters; specifically, streams need to distribute at least 1 GYD, the time frame needs to be between 1 hour and 5 years, and there can be at most 10 active or pending streams in total.

sGYD is upgradable by protocol governance. The Distributor and L2Distributor contracts are not upgradable. All of these contracts follow a role-based access control model with the governance system as the administrator.
