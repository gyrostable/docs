---
description: >-
  Lean governance processes that are held in check by bestowing protocol users
  with veto rights
---

# Optimistic Approval

Optimistic Approval is a new governance primitive that allows governance changes to be conditional on a timelock and veto process. It is a very flexible mechanism that can be used both to streamline governance processes and to better align incentives among protocol participants, not just in Gyroscope but also in DeFi governance more broadly.

Read our research piece introducing Optimistic Approval [here](https://ournetwork.substack.com/p/our-network-deep-dive-2).

Optimistic Approval can help to align incentives among different types of parties: one who possesses governance powers (governors), and another (guardians) who has the power to optionally veto during a timelock period. Ordinarily, guardians do not need to be involved in day-to-day governance, but the veto gives them the ability to block malicious proposals that would deviate from the vision of the protocol.

The Optimistic Approval framework generalizes who has governing powers and who has veto rights during a time delay. Additionally, the mechanism is parameterized by (1) initial timelock duration, (2) guardian voting threshold for increasing timelock duration, and (3) guardian voting threshold for achieving veto.

### Aligning Governance Incentives

In the first application to Gyroscope, Optimistic Approval is designed to give protocol users a veto power to stop governance changes that they disagree with. In this case, protocol users fulfill the guardian role of stewarding the protocol vision  (e.g., of maintaining stability). The mechanism introduces checks and balances on governors' power. Should governors try to deviate from the shared vision of the protocol, Gyro Dollar holders will be able to exercise optional veto powers during the time delay to stop it. Ordinarily, Gyro Dollar holders will not need to do anything if governance actions are sound. However, if governance actions are contentious, Gyro Dollar holders can exercise the veto to block the action.

{% hint style="info" %}
Optimistic Approval was initially devised this application as a means to circumvent an impossibility conjecture around secure decentralized governance arising from the models in our [Stablecoins 2.0 paper](https://arxiv.org/abs/2006.12388) (Conjecture 1).
{% endhint %}
