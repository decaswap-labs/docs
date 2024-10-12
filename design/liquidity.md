# Liquidity

### Adding Liquidity - All Pools

Users stream-add liquidity into the pool. The market should provide D if the asset being added is liquid. If it is not, then nobody will arbitrage, signalling the token is worthless. This will prevent the system being attacked by zombie coins, especially when it comes to allowing lending on all pools. There will be a small slippage as price to pay to add liquidity.&#x20;

LP Ownership units (internal mappings) are based on deposited assets compared with existing units. Users never have a claim on the D Units, they can only claim the assets paired to it.&#x20;

<img src="../.gitbook/assets/file.excalidraw (9).svg" alt="" class="gitbook-drawing">

### Removing Liquidity

Users remove liquidity by redeeming their liquidity shares `P'` which stream removes their claim on the liquidity. Arbitrage should re-balance the pools throughout.&#x20;

```
A' = A * P' / P
D` = D * P' / P -> Stream to A*
```

<img src="../.gitbook/assets/file.excalidraw (10).svg" alt="" class="gitbook-drawing">
