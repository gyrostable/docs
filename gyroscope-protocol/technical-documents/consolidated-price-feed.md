---
description: Details about how to interact with the consolidated price feed
---

# Consolidated price feed

## Interacting with the price feed

The main function to retrieve prices from with the consolidated price feed is:

```solidity
function getPricesUSD(address[] tokenAddresses) view returns (uint256[])
```

It expectes an array of asset addresses and returns an array of prices, denominated in USD.

### Example

Here is an example to retrieve the prices of (wrapped) Bitcoin and USDC. Note that this uses the Polygon asset addresses.

{% tabs %}
{% tab title="Solidity" %}
```solidity
interface IConsolidatedPriceFeed {
    function getPricesUSD(address[] memory baseAssets) external view returns (uint256[] memory);
}

address oracle = IConsolidatedPriceFeed(0xBa116c6f9e631413847747dF3cF6Dc5cDD1455C7);

address[] memory assets = new address[](2);
assets[0] = 0x1BFD67037B42Cf73acF2047067bd4F2C47D9BfD6; // WBTC
assets[1] = 0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174; // USDC
uint256[] memory prices = oracle.getPricesUSD(assets);
```
{% endtab %}

{% tab title="JavaScript (ethers)" %}
```javascript
const ethers = require("ethers");
const provider = new ethers.providers.JsonRpcProvider("https://polygon-rpc.com");
const oracleAddress = "0xBa116c6f9e631413847747dF3cF6Dc5cDD1455C7";
const oracleAbi = [
  "function getPricesUSD(address[] tokenAddresses) view returns (uint256[])"
];

const oracle = new ethers.Contract(oracleAddress, oracleAbi, provider);

const assets = [
  "0x1BFD67037B42Cf73acF2047067bd4F2C47D9BfD6", // WBTC
  "0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174" // USDC
];
const prices = await oracle.getPricesUSD(assets);
console.log(prices);
```
{% endtab %}
{% endtabs %}

## Deployed contracts

The consolidated price feed is currently deployed on the following networks:

* Polygon mainnet: [0xBa116c6f9e631413847747dF3cF6Dc5cDD1455C7](https://polygonscan.com/address/0xBa116c6f9e631413847747dF3cF6Dc5cDD1455C7)

