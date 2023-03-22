---
description: Key error codes of the Gyro Proto DSM
---

# DSM error codes

#### 2: Too much slippage

The returned minted GYD token or redeemed vault token would be below the minimum amount as set by the user’s slippage tolerance.

#### 45: Root price not grounded

Oracle safety check for absolute price levels failed. This occurs when different data sources quote significantly different values for the price of ETH even after removing outliers. This may point to&#x20;

(a) oracle manipulation or oracle quality issues,&#x20;

(b) simultaneous and non-uniform depegging of multiple stablecoins, or&#x20;

(c) a situation of extremely volatile and uncertain market prices.

#### 52: Not safe to mint

User is attempting to mint and the safety checks protecting reserve composition fail. This happens when one or more of the following is true:

* Case 1
  * User is attempting to mint with LP tokens where at least one underlying stablecoin asset is off-peg
  * and&#x20;
  * the user’s basket of collateral assets for the GYD mint increases the value of the vault for which the vault asset is backed by an off-peg stablecoin, relative to the value of the other vaults (i.e. increases the vault’s weight in the reserve).
* Case 2
  * The user’s basket of collateral assets for the GYD mint results in the value of at least one of the vaults falling outside of an allowed deviation, relative to the value of the other vaults (i.e. takes the vault weight outside of an allowed deviation from the target vault weight).&#x20;
  * And
  * The user’s basket of collateral assets for the GYD mint does not cause the weight of the vault outside the allowable range to move towards the target weight (and therefore closer to, or inside, the allowable range).

#### 53: Not safe to redeem

User is attempting to redeem and the basket of collateral assets for which the user is redeeming GYD causes the weight of at least one vault to move outside the allowed range and further away from target weight.&#x20;

#### 55: Token prices too small

For one of the reserve vaults in a mint or redeem operation, all involved tokens have prices close to 0. This error is raised to protect against exploits via numerical error because pricing such vaults can be very inaccurate.

#### 56: Trying to redeem more than the vault contains

The user is trying to redeem GYD for more vault assets than the vault contains.

#### 60: Vault flow too high

The mint or redeem operation would exceed the short-term limits on in-/outflow of at least one involved vault. These limits are put in place to limit the exposure of reserve vaults to unknown exploits.&#x20;

#### 61: Operation succeeds but safety mode activated

This is not an error but an informational message emitted in a SafetyStatus event. For at least one vault of a mint or redeem operation, the short-term flow limits have not been exceeded, but the operation has brought the in-/outflow close to its limit. As a safety measure, a time-locked safety mode was activated where minting/redeeming (depending on the direction of the flow) to/from this vault is disabled.

#### 64: Supply cap exceeded

The user is attempting to mint more GYD than their mint allowance. This is only relevant for the capped Gyro Proto system.

#### 65: Safety mode activated

For at least one vault in the mint/redeem operation, the safety mode is active and mint/redeem operations are disabled. The safety mode may previously have activated automatically due to high flows (see error 61) or it may have been activated by an oracle guardian. Note that the safety mode is directional; e.g., it may be the case that minting is disabled, but redemptions are not.\
