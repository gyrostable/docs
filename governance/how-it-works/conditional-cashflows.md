# Conditional cashflows

An important ability of governance is to be a good steward of the GYD reserve structure, adapting it as the DeFi space changes. Long-term, the decentralised Gyroscope system may generate operational cash flows. A key design component is to structure such cash flows to incentivise good stewardship aligned with the longterm system and disincentivize short-termism.

_Conditional Cashflows_ is a mechanism that places governors in a role that receives rewards related to system health into the future. The mechanism works by retaining operational cash flows in the protocol reserve and unlocking rewards related to these cash flows to governors at future times if the system remains healthy. Should the system become unhealthy, the cash flows are by default retained to maintain health. Governors, who have the important role of managing and curating the protocol reserve, are disincentivised from making risky decisions, since it puts their current rewards at risk (compare to bankers who don't have to return their bonus if the bank collapses).

This mechanism is implemented in `ReserveStewardshipIncentives` in the `Protocol` repository as it requires integration with the protocol code.

Governance can initiate an incentive initiative by calling `startInitiative`. To start an initiative, it is required that the system has excessive health properties (e.g., that the reserve ratio is above an excess threshold). Specifying an initiative includes specifying a `rewardPercentage`.

Once an initiative is active, several health properties of the system are tracked over a long period of time, as performed via `_checkpoint`. This includes tracking the average GYD supply and the number of days that reserve health violations are observed over this time period.

At the end of the time period, governance can call `completeInitiative`, which verifies whether health properties were achieved over the term of the initiative and, if so, calculates an incentive reward based on `rewardPercentage` and the average GYD supply over the term. The size of the reward is limited by a condition on the health of the system that would follow any reward. If `rewardPercentage` is too high considering the end health of the system, the reward calculation also imposes a penalty, reducing the size of the end reward.

The end result is intended to be a structure in which incentive rewards are only given to governance after their stewardship has proven successful over a long time period.
