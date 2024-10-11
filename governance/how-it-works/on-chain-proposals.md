# Proposals

## Lifecycle of a proposal

1. Proposal creation: A proposal, which is a list of calls to execute, is created by a participant using `GovernanceManager.createProposal`
   1. The tier (containing quorum and other metadata, see `DataTypes.Tier`) is set to the highest tier of any of the calls to execute
   2. The proposer votes are computed and checked against the proposal threshold (part of the tier information)
   3. If the proposer has enough voting power, the proposal is started
2. Voting phase
   1. Any participant with voting power is allowed to vote "for", "against", or "abstain" using `GovernanceManager.vote`
   2. A participant can change his/her vote at any time
3. Proposal conclusion: a vote can be concluded by anyone using `GovernanceManager.tallyVote`
   1. If the quorum is reached and the vote threshold is reached, the proposal is queued for execution
   2. If not, the proposal is marked as rejected
4. Proposal execution: a proposal can be executed by anyone using `GovernanceManager.executeProposal` once the time lock for the tallied proposal has passed
