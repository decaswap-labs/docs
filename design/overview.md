# Overview

## Liquidity

### External Pools

Liquidity is provided into pools only via external assets, matched to an internal, arbitrary, unit of account referred to as “D”. Pool LPs thus own dual-sided liquidity, but they can never withdraw D from the system or sell it. Since D has a programmatic supply and can only be bought as more LPs join the system, D should outperform most of the assets. This stops all value-leakage, and all speculation on the D asset is captured by the system itself - which is enjoyed by LPs themselves.&#x20;

Deposited liquidity is streamed in, which acquires the `D` asset through arbitrage against all other pools. The reverse happens when liquidity is removed. Since D is matched to all pools, flows across pools simply move the D between, but D never leaves the contract.

<img src="../.gitbook/assets/file.excalidraw (5).svg" alt="" class="gitbook-drawing">

{% hint style="warning" %}
If a zombie asset is added, no arbitrage will occur and the LP will experience negative slip on their own assets.&#x20;
{% endhint %}

{% hint style="info" %}
&#x20;LPs cannot hold D, so when they deposit, they are taking up a short position of their asset versus {everything else} and are notionally long the volatility of that pool. Because of this, it makes sense to only pay the LP in USDC, and separate the principle from the yield.&#x20;
{% endhint %}

<img src="../.gitbook/assets/file.excalidraw (6).svg" alt="" class="gitbook-drawing">

### Global Pool

There is a mechanism to become a “Global LP” which simply involves streaming from any listed pool into a Global Pool. The Global Pool participants earn half of Global Income (from all pools) and experience an Impermanent Loss/Gain which is correlated to the performance of the system as a whole.&#x20;

<img src="../.gitbook/assets/file.excalidraw (4) (1).svg" alt="" class="gitbook-drawing">

## Swaps

Swapping from any asset to any other asset causes it to be streamed across the pool, aggregated in the outgoing asset and then sent to the user. Fees are collected during the stream and at conclusion of the swap.&#x20;

The stream is computed to be the lower bound of the swap size against the pool depths to minimise slippage to no more than 10 BPS.&#x20;

Swapping assets cause an internal movement of `D` from one pool to another; which will cause counter-arb to re-balance.&#x20;

<img src="../.gitbook/assets/file.excalidraw (23).svg" alt="" class="gitbook-drawing">

The system also supports price-conditional streaming swaps.&#x20;

## Lending

Lending is enabled in order to maximise attractiveness of the system to users and increase the yields to Liquidty Providers. LPs lend out their assets to borrowers (and underwrite their collateral), but borrowers pay an interest rate back to LPs depending on System Utilisation.&#x20;

<img src="../.gitbook/assets/file.excalidraw (25).svg" alt="" class="gitbook-drawing">

###

