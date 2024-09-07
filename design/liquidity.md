# Pool Mechanics

### Adding Liquidity

Users deposit assets which insta-mint D Liquidity Units at the current pool-price and are placed into the pool as an LP. Their Ownership units (internal mappings) are based on deposited assets compared with existing units. Users never have a claim on the D Units, they can only claim the assets paired to it. All new LPs are locked for 7-days to stop attacks.&#x20;



<img src="../.gitbook/assets/file.excalidraw (3).svg" alt="" class="gitbook-drawing">

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
