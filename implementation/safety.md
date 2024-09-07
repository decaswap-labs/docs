# Safety

### Safety

Admin can emergency pause the router with granularity:

* Pause Liquidity Add
* Pause Liquidity Remove
* Pause Liquidity All
* Pause Swaps
* Pause Limit Orders
* Pause DVault
* Pause DECADAO
* Pause Lending Borrow
* Pause Lending Repay
* Pause Lending All
* Pause Rewards
* Pause Fees

### Upgradeability

Owner (or Admin), can upgrade at any time, by deploying and setting the upgraded contract addresses:

* Router
* Logic
* Utils
* DECADAO

### Fund Access

Owner can perform the following fund movements:

* Withdraw Fees from Fee Contract
* Move Unclaimed Rewards from a Pool Allocation back to the Reserve
* Withdraw the DECAMint Reserve

But it cannot:

* Withdraw Pool Assets (including DVault)
* Withdraw DECADAO assets

### Invariants

Since the owner can change the Router & Logic contracts, it can set a new Router & Logic contract that can perform attacks on the Pools Contract. Since all actions on the Pools Contract are essentially swaps (DECADAO, DECAVault, lending all wrap swap logic), then invariants can be set that disallow any external logic that breaks the following:

1. A swap cannot be made to D tokens, unless internally to DVault.&#x20;
2. Swaps must start and end at an external listed pool.&#x20;
3. All swaps must not send out any assets greater in value that deposited assets, as priced by moved D tokens.&#x20;
4. Remove liquidity does not send out assets greater than double the original claim on D Tokens.
