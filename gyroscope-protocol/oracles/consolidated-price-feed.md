# Consolidated price feed

## **Introduction**

Whereas projects typically rely on data feeds from an oracle provider, such as Chainlink, the Consolidated Price Feed (CPF) design layers and cross-references different oracle and on-chain data sources.

In effect, multiple consistency checks are applied that reference multiple, deep on-chain markets, which adds a quantifiable cost to manipulating price feeds. At the heart of these checks is the idea to define a relative price level via on-chain references to AMMs and then ground that price level by cross-referencing it against a variety of oracles.

{% hint style="info" %}
A respective technical paper and specification will be published at a later point.
{% endhint %}

## Advantages

The main advantages of the CPF oracle design are:

* Hardened security assumptions: by triangulating prices across many sources, discrepancies can be quickly detected on-chain without having to rely on trusted set-ups.
* Abstract away complexity: both in relation to handling TWAPs of AMMs (e.g. Uniswap), as well as in relation to the computation of relative price levels. Oftentimes, AMMs may take the price of a stablecoin as a proxy oracle. This is a hidden complexity that can be addressed with our proposed oracle design.
* Higher ‘return on investment’: prices confirmed by our method may be stored and thus made available (for similar costs as TWAPs) without re-accessing various oracles and re-computing prices.
* Ease of use: easy verification and ‘one-stop-access’ to robust price feeds. Any project with an existing Chainlink integration could decide to add the proposed consistency checks to strengthen their price feeds. This may be thought of as adding ‘assert’ like function logic, as the system can detect if individual components have broken.
