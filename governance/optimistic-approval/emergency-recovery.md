# Emergency Recovery

An emergency recovery mechanism for the governance contract is included as a fallback in case something goes wrong with the governance contracts and they are no longer usable (e.g, if they are bricked because of a smart contract bug or incorrect parameterization change).&#x20;

The emergency recovery mechanism is composed of a backup multisig combined with an optimistic approval mechanism and various safeguards as implemented in `EmergencyRecovery`.

The emergency recovery mechanism has the following properties:

* Multisig signers are assigned by governance and can be changed at any time
* The multisig can initiate an upgrade to the governance contract subject to a timelock
* (Optimistic approval) during the timelock, governance can vote to override the upgrade
* Emergency recovery has a sunset built in, which can optionally be extended by governance
