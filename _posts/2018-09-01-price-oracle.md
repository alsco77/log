---
title: "Leveraging Bancor to provide on chain ERC20 price oracle"
layout: post
date: 2018-09-01 14:40
image: /assets/images/thumbnails/bancor.png
headerImage: true 
hideTitle: false
wide: false
tag:
- Ethereum
- Solidity
- Truffle
category: project
subCategory: blockchain
---

## When
Sep 2018 - Sep 2018

## Links
[Github Repo](https://github.com/canyaio/canya-contracts-price-oracle)  
[Medium article](https://medium.com/canyacoin/canya-releases-hedged-escrow-to-protect-platform-users-from-price-volatility-7fca7a0aad32)

## What
Deployable Ethereum ERC20 Price Oracle for any currency listed on the Bancor Network.

This Oracle was made in order to calculate the price for CanYaCoin -> DAI (USD) in order to allow [CanWork](http://canwork.io)s hedged escrow system to operate - check out the [medium article](https://medium.com/canyacoin/canya-releases-hedged-escrow-to-protect-platform-users-from-price-volatility-7fca7a0aad32) for more details on the hedged escrow.

### Technicals
The final implementation is relatively straightforward - however distinguishing the mechanism and setting up the [test deployment](/assets/contracts/test_migration.js) with all required supplementary contracts to mimic a live BancorConverter required a reasonable work effort. Basically we:

 - Utilised the `getReturn` function from the generic [BancorConverter](/assets/contracts/BancorConverter.sol)

```solidity
    function getTokenToDai(uint256 _tokenAmount) external view returns (uint256) {
        uint256 decimals = MyERC20Token.decimals();
        uint256 valueOfOneToken = MyTokenConverter.getReturn(MyERC20Token, OracleBase.BNT(), 10 ** decimals);
        uint256 tokenValueInBNT = valueOfOneToken.mul(_tokenAmount).div(10 ** decimals);
        return OracleBase.getBNTDAIConversion(tokenValueInBNT);
    }
```
 - Deployed generic `base` contract to act as [BNT->DAI converter](/assets/contracts/ERC20PriceOracleBase.sol) to allow for multiple child oracles in the future
 - Deployed a `child` oracle to act as the [TOKEN->BNT converter](/assets/contracts/ERC20PriceOracle.sol), which, coupled with communication to the base oracle can carry out the full conversion

### Ensuring that the price lookup represented an accurate value
The nature of the conversion mechanism is such that the ratio between the volume of tokens held in the contract address is the rate. Thus, if we execute a high volume trade, this will affect the ratio and thus the conversion rate. Bancor does its best to account for this new rate of price as part of the calculation, even in theoretical lookup situations such as this. To get around that, we ran conversions for 1 token and then extrapolated the results.


### Utility
In order to provide an oracle for your token, you can easily use the deployment instructions given to deploy it onto the network.

For generalised or __future use__, with a few minor modifications it is possible for this oracle to be adapted such that it can look up any token connected to Bancor Network - provided the corresponding BancorConverter contract address. The method would accept the addresses of the token and bancor converter in question rather than having them baked into the contract. 

### Downsides of current implementation
 - The conversion relies on the Bancor network arbitrage system operating efficiently to represent an accurate value for BNT -> DAI
 - Should the Bancor converter upgrade and change addresses (at the permission of the token owner), the converter will also need to update to point at the new address






