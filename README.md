---
description: Overview of DECASWAP
---

# DECASWAP AMM

DECASWAP allows users to add assets into pools and earn passive yield paid in USDC. There are single-sided Pool LPs, as well as a Global LP of all pools at the same time - the DECAPOOL. The system controls the virtual balances of the paired asset - D Liquidity Units; which cannot be bought or held directly. Any asset can be added to the system if it achieves a minimum liquidity commitment.&#x20;

Pools use [THORChain's continuous liquidity design](https://docs.thorchain.org/thorchain-finance/continuous-liquidity-pools) with streaming swaps that allow it to be capital efficient; as well supporting limit orders - “price conditional swaps”. Deposits into the router automatically bump the swap queue, which is also exposed as a public keeper function. Bumping the swap queue allows anyone to claim fees. Opposite direction swaps are matched outside the swap queue. Due to this, and the fact that the swap queue cannot be re-ordered, most forms of MEV are avoided.&#x20;

An early-liquidation dynamic-interest lending scheme is supported with 50% LTV loans from pool collateral, borrowing from [THORChain's liquidity synthetic's idea](https://docs.thorchain.org/thorchain-finance/synthetic-asset-model). The collateral can be liquidated for a small fee below a liquidation price.&#x20;

There is a DECADAO that earn 10% System Income and control protocol parameters. The DECADAO controls the DECAMINT, a reserve that streams rewards to the LPs.&#x20;

<img src=".gitbook/assets/file.excalidraw (3).svg" alt="" class="gitbook-drawing">

DECASWAP borrows much of THORChain's novel ideas and imports them to the EVM. DECASWAP is built by a co-founder of THORChain.&#x20;

1. Continuous Liquidity
2. Streaming Swaps
3. Price Conditional Swaps
4. Global LP
5. Liquidity Synthetics
6. Lending Scheme via Mint

