# Fees

### Do we want to hijack people's EOA transactions to run the keeper queue: No

If someone swapping `swap(token token)`, then we may as well use that swap, to "bump the queue".

Or do we leave "bump the queue" to the keeper bot. Yes



When someone swaps, they simply "deposit" their swap, and hand it over to the keeper bots.&#x20;



Msg.sender has a mapping with USDC to claim&#x20;



### Processing

Keeper fees: accrue to `msg.sender`

Liquidity fees: pay into the system income



1\) 15BPS outbound fee on processed swaps&#x20;

2\) 5BPS stream fee to pay&#x20;



Keepers Fees&#x20;

1\) Can stay in pool contract to minimise gas costs&#x20;

2\) Accrued in USDC (ideally)&#x20;

3\) Pay 10% to DECA stakers, 45% to global LP, and 45% to pool LP (of the outbound asset)&#x20;



Stream Fees&#x20;

1\) All streams go via D. Charge 20BPS in D per stream, before moving from D1 to D2.&#x20;

2\) At end of execution, D is accumulated from all streams, so swap D to USDC&#x20;

3\) Allocate 1/3 to `msg.sender` ie, the keeper.bot&#x20;

4\) Allocate 1/10 of remaining to DECA pool LP 5) Allocate 1/2 of remaining to DPool LP&#x20;

6\) Allocate rest to transferOut asset Pool LP Since Pool Contract has the mappings of assets, pool LP, global LP, then let everyone claim directly from pool contract `claimFees(pool)`
