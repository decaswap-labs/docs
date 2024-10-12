# Fees

#### Keeper Fees&#x20;

Every stream, pay the keeper 5BPS.

1. Keep in pool contract to minimise gas costs&#x20;
2. &#x20;Accrued in D per stream, swap to USDC, allocate to `msg.sender`

#### Liquidity Fees&#x20;



2\) At end of execution, D is accumulated from all streams, so swap D to USDC&#x20;

3\) Allocate 1/3 to `msg.sender` ie, the keeper.bot&#x20;

4\) Allocate 1/10 of remaining to DECA pool LP 5) Allocate 1/2 of remaining to DPool LP&#x20;

6\) Allocate rest to transferOut asset Pool LP Since Pool Contract has the mappings of assets, pool LP, global LP, then let everyone claim directly from pool contract `claimFees(pool)`
