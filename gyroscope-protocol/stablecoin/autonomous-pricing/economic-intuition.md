---
description: Intuition behind autonomous price-stability mechanism
---

# Economic intuition

## Overview <a href="#e55d" id="e55d"></a>

The Gyroscope reserve is designed to serve as an all-weather portfolio, diversifying not just price risk but also counterparty, censorship, and regulatory risks. In doing so, it maintains the original value propositions of DeFi.

Note that the reserve is not maintained by any counterparty or custodian. Assets are held in permissionless and non-custodial smart contracts.

However, no crypto portfolio cannot completely diversify these risks, and shocks to reserve assets are still possible. As such, Gyroscope is explicitly designed to deter speculative attacks on the peg in case such shocks affect reserve health. By default, it aims to be slightly over 100% reserved in a robust array of assets (the first line of defense of the all-weather reserve). It maintains additional mechanisms, however, in case shocks affect the reserve.

In times of crisis, it aims to make it in users’ interest to wait to redeem rather than sell at below par-value. By waiting, users will get a more favourable redemption rate. In turn, this makes any speculative attack less profitable.

At the heart of this design is a formal economic game. The intuition is as follows:

> Users form beliefs about the fundamental value of the stablecoin. These are based on the value of the reserve and how widely accepted and used the stablecoin is. But users also form beliefs about the beliefs of other market-participants (and so on). **G**_**yroscope coordinates these beliefs**_. Since the value of the reserve is observable on-chain, as well as the rules governing how it will be used, rational users can implicitly agree on whether to attack or defend the peg since they _**only win by being in the majority.**_

As a result, with a big enough reserve and with enough acceptance of the stablecoin, the value of the stablecoin will be stable at $1 in a wide range of market conditions. While the peg could break in extreme settings, by design the reserve is difficult to deplete in the short to medium run, and — provided the cryptocurrency ecosystem recovers — can eventually recover.
