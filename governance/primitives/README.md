---
description: Resilient governance primitives used in Gyroscope
---

# Governance primitives

{% hint style="info" %}
_These docs describe the Gyroscope design mechanisms as formulated through academic research and development. Gyroscope is designed to be fully decentralized, with the Gyro DAO responsible for deciding which mechanisms are incorporated into the final design and launching the Gyroscope system._
{% endhint %}

Gyroscope is designed to build a virtuous cycle between its different users: Gyro Dollar holders, governors, and passive liquidity providers (LPs).

![](<../../.gitbook/assets/Governance Flow Chart.png>)

Read on to learn how the Gyroscope design fosters this virtuous cycle.

### **Governance Today is Not Safu**

Like politicians and bankers, governors in DeFi systems can be short-sighted, focusing on immediate payoffs rather than the long-term. They can also be outright malicious, especially in DeFi where governors are practically anonymous. We term these issues of short-termism and malicious exploits as _governance extractable value_ (GEV), which need to be minimized to maintain a secure DeFi protocol. Read more in our recent [GEV article](https://ournetwork.substack.com/p/our-network-deep-dive-2) and in our our [DeFi paper](https://arxiv.org/abs/2101.08778) (Sections V.C and VI.B).

### **Governance Reinvented**

Motivated by academic research, Gyroscope proposes several new governance mechanisms that help to align governors with the long-term interests of the protocol by minimizing GEV.

How? In any functional stablecoin, someone always pays \~$1 for each newly minted stablecoin. Where this $1 goes is critical. In designs today, part or all of this dollar goes into someone’s pocket: e.g., shareholders in seigniorage shares designs. For the long-term interest of the protocol, this is a mistake. It reduces governors’ skin in the game whereas it is better to increase it. As long as farming yields are big enough in the short-term, they have no reason to care about the small stake they stand to lose if they don’t get out in time.

The Gyroscope design is different. Long-term, the decentralized Gyroscope system may generate operational cash flows. A key design question is how these cash flows can be distributed to incentivize agents. Gyroscope proposes a new governance primitive called _Conditional Cashflows_, which places governors in a role that receives rewards related to system health into the future. The mechanism works by retaining operational cash flows in the protocol reserve and unlocking rewards related to these cash flows to governors at future times if the system remains healthy. Should the system become unhealthy, the cash flows are by default retained to maintain health. Governors, who have the important role of managing and curating the protocol reserve, are disincentivised from making risky decisions, since it puts their current rewards at risk (compare to bankers who don't have to return their bonus if the bank collapses). If times are good, and governance token valuation is sky high, governors are incentivised to auction off new tokens early to boost the reserve.

But how do we know that governors can’t abuse their power in other ways? Gyroscope proposes another new governance primitive called _Optimistic Approval_, which steers governors to this path through a system of checks and balances. In this mechanism, if governors try to deviate from the shared vision of the protocol, Gyro Dollar holders can exercise optional veto powers during a time delay to stop it. Ordinarily, Gyro Dollar holders do not need to do anything if governance actions are sound. However, if governance actions are contentious, Gyro Dollar holders can exercise the option to veto, and if enough do, the action is blocked.

Gyroscope is about empowering the community to govern their own money, making its users its owners. It provides best-in-class mechanisms to bring this to life. Fairness and decentralization are top priorities in the governance token distribution.
