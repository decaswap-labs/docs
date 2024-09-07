# System Processing

## System Processing

The system requires on-going input to process the various mechanics. The users themselves can pay, or incentives are set up for bots to keep the system running.&#x20;

\


Swap Processing (WBTC-WETH)

1. Swap deposits process the Stream Queue first (up to a limit), then check the opposite pair for a matching order, then check the pending Swap Queue for a matching order. If a match is found, or a stream executes a processing swap, then transferOuts and fee collection is made.&#x20;
2. A keeper can bump any pair stream queue at any block. &#x20;

\


Pool Processing

1. Adding/Removing Liquidity, Depositing/Withdrawing DVault or Borrowing/Repaying Debt causes the Pool Queue to be bumped.&#x20;
2. Firstly Asset<>D streams are bumped, which includes borrow or repay streaming (which is a D to Asset stream).
3. Opposite D streams will cause matching and thus accelerated processing.&#x20;
4. Interest payments are also processed for that pool (deleting Synth Collateral).
5. A keeper can bump any pool at any block.&#x20;
6. There are no price-conditional swaps for D Streaming.&#x20;

\


Income Processing

1. Anyone claiming USDC income payments will first move accumulated Income Payments from the Pool Contract to the Income Contract and then collect their USDC.
2. Anyone claiming DECA rewards payments will first move accumulated rewards into the Income Contract, then collect their Rewards.
