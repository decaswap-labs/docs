---
description: There are two types of Pools.
---

# Liquidity

### Adding Liquidity - All Pools

Users stream-add liquidity into the pool. The market should provide D if the asset being added is liquid. If it is not, then nobody will arbitrage, signalling the token is worthless. This will prevent the system being attacked by zombie coins, especially when it comes to allowing lending on all pools. There will be a small slippage as price to pay to add liquidity.&#x20;

LP Ownership units (internal mappings) are based on deposited assets compared with existing units. Users never have a claim on the D Units, they can only claim the assets paired to it.&#x20;

All new LPs are locked for 7-days to stop attacks.&#x20;

<img src="../.gitbook/assets/file.excalidraw (9).svg" alt="" class="gitbook-drawing">

### Adding Liquidity - Blue Chip

Blue-chip pools are deemed to be safe to the system and are granted a privilege - they do not require D arbitrage. This is reserved for unmintable or pegged assets (WETH, WBTC, Stables). Blue-chip status can be revoked. Users deposit assets which insta-mint D Liquidity Units at the current pool-price and are placed into the pool as an LP.&#x20;

<img src="../.gitbook/assets/file.excalidraw (3) (1).svg" alt="" class="gitbook-drawing">

```
P' = P * A' / (A' + A)
D' = D * A' / (A' + A)
```

### Removing Liquidity

Users remove liquidity by redeeming their liquidity single-sided out to the asset. The paired D Units are simply insta-burnt. Even if D tokens move around the pools, when all LPs leave D Units should be 0.

```
A' = A * P' / P
```

<img src="../.gitbook/assets/file.excalidraw (10).svg" alt="" class="gitbook-drawing">
