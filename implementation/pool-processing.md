# Pool Processing

## Liquidity

### Pool Processing

1. For Add/Borrow, process Asset -> D stream queue first, charge stream fees in D, swap back to Asset deposit, then exit gas limit
2. For Deposit/Repay, process Asset -> D stream queue first, keep fees in D, add to swapAmountOut, then exit gas limit
3. For Remove/Withdraw, process D->Asset stream queue first, accumulate stream fees in Asset, then exit gas limit
4. Check for opposite swaps, if any, match and settle
5. Charge interest payments on Synth Collateral
6. Liquidates any bad debt

### Keeper Bot - Pool Queue

1. Nominates pool, direction, gas limit
2. Fees are 5BPS on all streams, 50BPS on bad debt.

<img src="../.gitbook/assets/file.excalidraw (1).svg" alt="" class="gitbook-drawing">

<img src="../.gitbook/assets/file.excalidraw (2).svg" alt="" class="gitbook-drawing">

