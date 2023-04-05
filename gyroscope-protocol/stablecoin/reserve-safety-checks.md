# Reserve Safety Checks

## The Basics

The Gyroscope Reserve is comprised of a set of vaults. When a user mints, the tokens they use to mint are transferred to the relevant vault(s), with the user receiving Gyro Dollars in return. When a user redeems, the selected number of Gyro Dollar units are burned in exchange for vault tokens.

To ensure that the Gyroscope Reserve remains diversified, each vault is given a target/ideal weight. For example, for a vault containing USDC/DAI, the ideal weight could be set to 20%: in the long-run, approximately 20% of the reserve's assets should be stored in that vault. Together, the ideal weights of each vault should sum to 100%.&#x20;

This page describes in detail how these vault weights are enforced.&#x20;

## Reserve Weights

The stablecoin system endeavours to keep the vaults to the correct proportions by keeping track of a number of different 'weights'.

* **Ideal weights**: these can be thought of as the 'target' weight for a particular vault. For example, the ideal weight of a USDC/DAI vault could be 20%.&#x20;
* **Current weights**: the actual/current weight of a vault. For example, if the total USD value of the reserve is 100 USD and one vault contains 35 USD, then the current weight of that vault would be 35%.
* **Resulting weights**: the weight for each vault that would result if a particular mint or redeem were to occur.

## Reserve Weight Epsilon

Each vault is permitted to deviate from the ideal weight by a percentage. For example, for a vault with an ideal weight of 20% may be allowed to vary by 10% from that ideal weight (so +/- 2% of the total reserve value). This permitted variation is what we call **epsilon**.

Now, assume that a user wants to mint some Gyro Dollars.

* If the resulting weights from the mint would be such that they are within epsilon of the ideal weights, then the mint would be considered safe;
* If one or more of the resulting weights would be outside of epsilon, then the operation would only be considered safe if the resulting weight would be closer to the ideal weight than the current weight is closer to the ideal. In other words, if the operation promotes the rebalancing of the vault back towards the ideal weight.&#x20;

## Stablecoin Deviations from Peg

Another type of safety check performed by Gyroscope centres on stablecoins that are in the reserve. For a vault where one of its underlying assets is a stablecoin, during minting a check is performed to ensure that the stablecoin is not off-peg beyond some tolerated margin (say, 0.98-1.02).&#x20;

A mint operation that attempted to deposit an off-peg stablecoin and mint Gyro Dollars could only succeed if the mint did not result in the vault containing the off-peg stablecoin decreasing in weight.&#x20;



