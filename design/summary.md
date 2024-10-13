# Summary



### Conclusion

DECASWAP AMM is design that has single-sided UX with a passive fee-earning experience. Streaming Swaps is what allows the system to stay competitive with CLAMM. If 15BPS is the target then a $10m swap on a $100m pool can be done in 67 blocks, which is 13 mins. Arbitrage and limit orders accelerates streaming speeds. A peer2pool lending scheme is also possible with the CFMM-based liquidity design since it can quote 0 to infinity and the borrowers both waive liquidity fees as well as pay an interest rate to LPs.

### MEV Resistance

The protocol has MEV (Miner Extractable Value) Resistance due to the following reasons:

1. All swaps are placed in a stream queue where they cannot be re-ordered.&#x20;
2. All swaps are streamed such they generate a maximum of 10BPS slippage on pools, thus is too low for MEV to be attractive.&#x20;
3. There is no ability to pay for priority; since all swaps are ordered based on FIFO.&#x20;
4. Attempting to sandwich-attack a swap will only cause an attacker's streams to be executed in-turn and if back-run will simply be matched outside of the pool.



### Parameters

| Parameter       | Value | Description                                                                          |
| --------------- | ----- | ------------------------------------------------------------------------------------ |
| minSlipBPS      | 10    | Each swap is divided by `10/10000 = 1000` to compute the number of streams per swap. |
| keeperFeeBPS    | 5     | Keepers charge 5BPS to process each stream.                                          |
| liquidityFeeBPS | 15    | All completed swaps are charged this to pay the system.                              |
| poolShareBPS    | 4500  | 45% of the Fee retained in the pool.                                                 |
| systemFeeBPS    | 1000  | 10% of the Fee paid into the DECA pool                                               |
