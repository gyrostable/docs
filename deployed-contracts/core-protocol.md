---
description: '[Last updated 8 December 2023]'
---

# Core protocol

## Core Protocol

* `GYDToken`: [0xe07F9D810a48ab5c3c914BA3cA53AF14E4491e8A](https://etherscan.io/address/0xe07F9D810a48ab5c3c914BA3cA53AF14E4491e8A)
  * Implementation: [0xfa08eb3a781532f47b1dd811a6ca326842ea0cb5](https://etherscan.io/address/0xfa08eb3a781532f47b1dd811a6ca326842ea0cb5)
* `GyroConfig`: [0xaC89cc9d78BBAd7EB3a02601B4D65dAa1f908aA6](https://etherscan.io/address/0xaC89cc9d78BBAd7EB3a02601B4D65dAa1f908aA6)
  * Implementation: [0xe0074199dda10dafbd267cf01cc6e6ed3d45986b](https://etherscan.io/address/0xe0074199dda10dafbd267cf01cc6e6ed3d45986b)
* `Motherboard`: [0x8De76bF863E0A571be7165d9c85A1116c0fFf393](https://etherscan.io/address/0x8De76bF863E0A571be7165d9c85A1116c0fFf393)
  * Implementation: [0xBaF6A0bE2DCA3350D3558783740dd8d540A6CC95](https://etherscan.io/address/0xBaF6A0bE2DCA3350D3558783740dd8d540A6CC95)
* `PrimaryAMMV1`: [0xE7eA594b5905eC0dd321E61d7625711B635a6Ce5](https://etherscan.io/address/0xE7eA594b5905eC0dd321E61d7625711B635a6Ce5)
* `ReserveManager`: [0x2519A729535470830D345b78109818F94C1c2869](https://etherscan.io/address/0x2519A729535470830D345b78109818F94C1c2869)
* `VaultRegistry`: [0xf2865bf37c820af6FE3A1b4a0B92fa050aEd4eB5](https://etherscan.io/address/0xf2865bf37c820af6FE3A1b4a0B92fa050aEd4eB5)
  * Implementation: [0x82c45c1b7B798aA152937107058c8098630B5A22](https://etherscan.io/address/0x82c45c1b7B798aA152937107058c8098630B5A22)
* `AssetRegistry`: [0x66a7aA37Ea714e0B8DD553F375104Ea7D160b0B2](https://etherscan.io/address/0x66a7aA37Ea714e0B8DD553F375104Ea7D160b0B2)
  * Implementation: [0x94c34174f484cc0C80eA2d3670A50eC9325C9126](https://etherscan.io/address/0x94c34174f484cc0C80eA2d3670A50eC9325C9126)
* `Reserve`: [0xc7ab175954B1211f93209CA9fc89faFc3FB21a37](https://etherscan.io/address/0xc7ab175954B1211f93209CA9fc89faFc3FB21a37)
  * Implementation: [0x00FfBaEAaCAE63a295A23C7BD2C2A9193D435c2A](https://etherscan.io/address/0x00FfBaEAaCAE63a295A23C7BD2C2A9193D435c2A)
* `StaticPercentageFeeHandler`: [0x757cFCf4Fec346E4880Ec686d11BEA60c8f9a051](https://etherscan.io/address/0x757cFCf4Fec346E4880Ec686d11BEA60c8f9a051)
* `ReserveStewardshipIncentives`: [0x5C73d4E5349ffD392e62fa6BeD994bB449D94F86](https://etherscan.io/address/0x5C73d4E5349ffD392e62fa6BeD994bB449D94F86)
* `GydRecovery`: [0x2A803cE12bE775802a7c6f50797e53E9C3Fd4025](https://etherscan.io/address/0x2A803cE12bE775802a7c6f50797e53E9C3Fd4025)

## Authentication

* `ProxyAdmin`: [0x581aE43498196e3Dc274F3F23FF7718d287BC2C6](https://etherscan.io/address/0x581aE43498196e3Dc274F3F23FF7718d287BC2C6)
* `GovernanceProxy` (to be deprecated): [0x4f244fcAfF67A2F98EaeC20a44CAF079A7f7A1D4](https://etherscan.io/address/0x4f244fcAfF67A2F98EaeC20a44CAF079A7f7A1D4)

## Safety checks

* `RootSafetyCheck`: [0x56773CA4A4138F21128d23ADB237004697273789](https://etherscan.io/address/0x56773CA4A4138F21128d23ADB237004697273789)
* `VaultSafetyMode`: [0x84B22e0f83d848eaD9fC050734e946b665232c0e](https://etherscan.io/address/0x84B22e0f83d848eaD9fC050734e946b665232c0e)
* `ReserveSafetyManager`: [0x8f38321416d587Ec4F3A4b37b1CcBB80013a3FAb](https://etherscan.io/address/0x8f38321416d587Ec4F3A4b37b1CcBB80013a3FAb)

## Reserve vaults

* `BalancerPoolVault` - ECLP LUSD/crvUSD: [0x29609B3fD68C647c3a619e69DE386F2F02Ee26e6](https://etherscan.io/address/0x29609B3fD68C647c3a619e69DE386F2F02Ee26e6)
  * Implementation: [0x86858b3d33e01842715a5c9c757dE9f7E18e3390](https://etherscan.io/address/0x86858b3d33e01842715a5c9c757dE9f7E18e3390)
* `BalancerPoolVault` - ECLP USDP/GUSD: [0x8E17873fe6C257Fcd4b32777658914B4B1a94fF2](https://etherscan.io/address/0x8E17873fe6C257Fcd4b32777658914B4B1a94fF2) (unused)
  * Implementation: [0x77F2Aeb44088cdb35F6D3070dC072C56Ff5e0014](https://etherscan.io/address/0x77F2Aeb44088cdb35F6D3070dC072C56Ff5e0014)
* `GenericVault` - fUSDC: [0x88F3b40E45213131860F81b32CA12a3d54821d65](https://etherscan.io/address/0x88F3b40E45213131860F81b32CA12a3d54821d65)
  * Implementation: [0x80eCF3d96446AB3abAF3D037d1b352bb41295176](https://etherscan.io/address/0x80eCF3d96446AB3abAF3D037d1b352bb41295176)
* `GenericVault` - sDAI: [0x830913c917B07311EAE53687BE27C1c0B589aB31](https://etherscan.io/address/0x830913c917B07311EAE53687BE27C1c0B589aB31)
  * Implementation: [0x80eCF3d96446AB3abAF3D037d1b352bb41295176](https://etherscan.io/address/0x80eCF3d96446AB3abAF3D037d1b352bb41295176)
* `GenericVault` - aUSDT: [0x98962bEC8Bf0363D00D97D9049B40079356A4953](https://etherscan.io/address/0x98962bEC8Bf0363D00D97D9049B40079356A4953)
  * Implementation: [0x80eCF3d96446AB3abAF3D037d1b352bb41295176](https://etherscan.io/address/0x80eCF3d96446AB3abAF3D037d1b352bb41295176)

## Consolidated Price Feed

* `BatchVaultPriceOracle`: [0x46412cdEC90b266629bf05188185E9fD109EC881](https://etherscan.io/address/0x46412cdEC90b266629bf05188185E9fD109EC881)
* `ChainlinkPriceOracle`: [0xa2b76e60215617e676c6a0041B26a7C3C126DB5E](https://etherscan.io/address/0xa2b76e60215617e676c6a0041B26a7C3C126DB5E)
* `CheckedPriceOracle`: [0x2a18F596283f9082Fd88F82556d5F78E3c482411](https://etherscan.io/address/0x2a18F596283f9082Fd88F82556d5F78E3c482411)
* `TrustedSignerPriceOracle`: [0xf4cA93C70a00032856e6d942Be2eB1cea54b4Aa5](https://etherscan.io/address/0xf4cA93C70a00032856e6d942Be2eB1cea54b4Aa5)
* `ConstantRateProvider`: [0x5413E8e572759787FBEcE0A8e8d65EB5188556d8](https://etherscan.io/address/0x5413E8e572759787FBEcE0A8e8d65EB5188556d8)
* `RateManager`: [0xdbc810d748f808967F34da2f37f116c58EC4eDA7](https://etherscan.io/address/0xdbc810d748f808967F34da2f37f116c58EC4eDA7)
* `GenericVaultPriceOracle`: [0x89B93862beBBA6c98E6f158ef9FadA004FDE854A](https://etherscan.io/address/0x89B93862beBBA6c98E6f158ef9FadA004FDE854A)
* `Balancer2CLPPriceOracle`: [0xCF9CDdB1dD40c1C1476E896AE2263934fc18dd10](https://etherscan.io/address/0xCF9CDdB1dD40c1C1476E896AE2263934fc18dd10)
* `Balancer3CLPPriceOracle`: [0x4Bd408099486600234A91851582c969470A78039](https://etherscan.io/address/0x4Bd408099486600234A91851582c969470A78039)
* `BalancerCPMMPriceOracle`: [0xc0682b356ab9115F2cB4Dd0d9A471143f46a5Ff5](https://etherscan.io/address/0xc0682b356ab9115F2cB4Dd0d9A471143f46a5Ff5)
* `BalancerECLPPriceOracle`: [0x21cE2C302fFeFe0C1f601156A1E2c54eF4C0D094](https://etherscan.io/address/0x21cE2C302fFeFe0C1f601156A1E2c54eF4C0D094)
* `TellorOracle`: [0xe22188F5d6ACc1dd951Bd20F531624b690F9D9a0](https://etherscan.io/address/0xe22188F5d6ACc1dd951Bd20F531624b690F9D9a0)
* `UniswapV3TwapOracle`: [0x5AdA07Ff0d2772E202776be8a8EC69ac3345050f](https://etherscan.io/address/0x5AdA07Ff0d2772E202776be8a8EC69ac3345050f)

## SAMMs

* `GYD/sDAI`: [0x1CCE5169bDe03f3d5aD0206f6BD057953539DAE6](https://etherscan.io/address/0x1CCE5169bDe03f3d5aD0206f6BD057953539DAE6)
* `GYD/USDC`: [0xC2AA60465BfFa1A88f5bA471a59cA0435c3ec5c1](https://etherscan.io/address/0xC2AA60465BfFa1A88f5bA471a59cA0435c3ec5c1)
* `GYD/USDT` [0xfbfaD5fa9E99081da6461F36f229B5cC88A64c63](https://etherscan.io/address/0xfbfaD5fa9E99081da6461F36f229B5cC88A64c63)
