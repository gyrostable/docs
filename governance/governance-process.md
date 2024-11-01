# Governance process

## Outline

This page describes the process that should be followed to take an idea to implementation through the Gyroscope governance system.

**Step 1:** Consultation, discussion and revision

**Step 2:** Indicative vote on Snapshot&#x20;

**Step 3:** Final on-chain vote

## Step 1 - Consultation

Anyone can think of an idea and write it up as a post in the Gyroscope Improvement Proposals section of the [Gyroscope Forum](https://forum.gyro.finance/c/gip/6).

**Guidelines**

1. The title should be in the format “\[Consultation] -  Topic”
2. The body should contain the following sections:
   1. **Background/motivation**
   2. **Summary of proposal**: A clear and easy to understand description of the proposed change, and how the change would affect the protocol
   3. **Risk assessment**: an explanation of the risks to the protocol involved in the proposed change

**Timeline**

1. The Consultation phase should last for a minimum of 72 hours before moving to an indicative vote on Snapshot.&#x20;
2. Any Gyroscope Governance participant with more than 10 GGU can extend the minimum consultation time period to 7 days. This is to allow more consultation time for potentially complex topics if needed.
3. If the Consultation goes stale or the creator of the proposal does not create a Snapshot proposal, after 4 weeks elapses the post will be closed.&#x20;

## Step 2 - Snapshot Vote

**Requirements**

1. Following Step 1, To be able create a Snapshot Proposal in the [Gyroscope Governance space](https://snapshot.org/#/gyrodao.eth), the creator needs to have at least 3 GGU.&#x20;

**Guidelines**

1. The title should be one of two formats:
   1. If the proposal is for an **off-chain change** to Gyroscope, and therefore the final vote, the title should be in the format “\[GIP-xxx] -  Topic”
   2. If the proposal is for an **on-chain change**, the title should be in the format “\[Indicative Vote] -  Topic”. The vote is indicative because in order for any change to be enacted on-chain, it will need to pass an on-chain governance vote. The set of eligible voters is the same.
2. The body should contain the following sections:
   1. **Background/motivation**
   2. **Summary of proposal**: A clear and easy to understand description of the proposed change, and how the change would affect the protocol
   3. **Feedback from Step 1,** which much include an explanation of how this was incorporated into the proposal.
   4. **Risk assessment**: an explanation of the risks to the protocol involved in the proposed change
   5. A link to the original Consultation in Step 1. Once created on Snapshot, a link to the Snapshot proposal should also be posted in the original Consultation proposal.

**Timeline**

1. Voting runs for 96 hours starting on Thursdays.
2. Quorum is set to 300 GGU for Indicative votes and higher for Final votes.&#x20;
3. If the vote passes with quorum:
   1. If the Snapshot vote is a \[GIP-xxx], then the DAO has now reached its decision and the off-chain change is recommended to be implemented.
   2. If the vote is an \[Indicative Vote] then move to Step 3 - Final on-chain vote.

## Step 3 - Final on-chain vote

**Guidelines**

1. A new post should be created on the [Gyroscope Governance forum](https://forum.gyro.finance/c/gip/6).
2. The title should be in the format “\[GIP-xxx] - Topic”
3. The body should contain the following sections:
   1. **Background/motivation**
   2. **Summary of proposal**: A clear and easy to understand description of the proposed change, and how the change would affect the protocol.
   3. **Risk assessment**: an explanation of the risks to the protocol involved in the proposed change
   4. **Links**:
      1. A link to a PR, opened in the relevant [Gyroscope repository](https://github.com/gyrostable), that would implement the change(s) as described in the proposal.
      2. A link to the Proposal, as implemented by the PR, on the Gyroscope Governance [dashboard](https://gov.gyro.finance/). Sufficient governance power in terms of GGU is needed to be able to create a proposal.
      3. A link to the original Consultation from Step 1.
      4. A link to the Indicative Vote from Step 2.

**Timeline**

Voting will then take place for a timeframe and with a quorum determined by the pre-set parameters.&#x20;

Once created, any participant is able to for "for", "against", or "abstain" on-chain. Votes can be changed at anytime. The vote tally can be triggered by anyone. If quorum and the vote threshold is reached, the proposal is queued for execution.&#x20;

For more details on the on-chain voting process, please see [here](how-it-works/on-chain-proposals.md).&#x20;
