# Streaming Swaps

Swap Deposit

1. A user deposits in a direction
2. Process outgoing streams first, accumulate fees in outgoing asset, then exit gasLimit&#x20;
3. Check for opposite swaps, if any, match and settle
4. If no opposite, check last index pending, if valid price, then move to Stream Queue&#x20;
5. Match, Settle
6. Transfer out Asset, send fees to System

Order Deposit

1. A user deposits in a direction, with price
2. If current price valid, then process as per Swap Deposit
3. If not valid, search pending Swap Queue, in reverse, looking for correct price to insert.&#x20;
4. Insert and re-order array.&#x20;

Keeper Bot - Swap Queue

1. Nominates pair, direction, gas limit
2. Starts at (2) above
3. Fees are 5BPS on all streams, accumulated in outgoing asset for the bot
4. Will do Stream Queue first, and also do the Pending Swap Queue.&#x20;

Pool Processing

1. For Add/Borrow, process Asset -> D stream queue first, charge stream fees in D, swap back to Asset deposit, then exit gas limit
2. For Deposit/Repay, process Asset -> D stream queue first, keep fees in D, add to swapAmountOut, then exit gas limit
3. For Remove/Withdraw, process D->Asset stream queue first, accumulate stream fees in Asset, then exit gas limit
4. Check for opposite swaps, if any, match and settle
5. Charge interest payments on Synth Collateral
6. Liquidates any bad debt

Keeper Bot - Pool Queue

1. Nominates pool, direction, gas limit
2. Starts at (2) above
3. Fees are 5BPS on all streams, 100BPS on bad debt.
