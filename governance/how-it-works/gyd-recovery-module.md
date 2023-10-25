# GYD Recovery Module

Any user can stake GYD in the GYD recovery module for use in the event that the stablecoin reserve ratio falls below some predefined threshold.&#x20;

The GYD recovery module is set up with liquidity mining infrastructure, so governance can choose to allocate incentive assets in the form of GYFI tokens to the recovery module and can start or stop the mining of these incentives by participants who have staked GYD in the module.

If the GYD stablecoin reserve ratio falls below a predefined trigger ratio, GYD in the recovery module is burned.&#x20;

* **Partial burn**. If there is enough GYD in the recovery module to bring the stablecoin system to its target reserve ratio, the corresponding amount of GYD will be burned. This is performed by modifying the `adjustmentFactor` affecting adjusted balances.&#x20;
* **Full burn**. A full burn is when all GYD in the module is burned and is handled separately.

<figure><img src="../../.gitbook/assets/GYD-Recovery-Module-Graphic.gif" alt=""><figcaption></figcaption></figure>

A user can initiate a withdrawal of their staked GYD subject to an unstaking period. Until a user completes their withdrawal following the unstaking period, their GYD remains at risk in the recovery module.

The contract tracks an adjusted form of balances that accounts for any recovery operations that are performed.
