# Lending

The lending design is an early-liquidation, dynamic-interest, no-expiry loan scheme using Liquidity Synths. Only participants in the lending scheme can hold Synths, so to receive a loan they must accept the terms of holding synths, which come with an interest rate.&#x20;

<img src="../.gitbook/assets/file.excalidraw (2) (1).svg" alt="" class="gitbook-drawing">

### Liquidity Synths&#x20;

Liquidity synths allow asset-denominated collateral to be stored in the pool liquidity. The pool liquidity can underwrite the asset-denominated collateral across a range of prices because pool liquidity is less volatile than a non-coupled asset. To mint a synth, users deposit assets into pools and D Units are insta-minted to match the deposit and their collateral is stored in units of asset deposited. There is a cap of 33% of the depth of the pool (in asset terms) that synths are allowed to be minted up to. When a user withdraws a Synth, the owed asset amount is taken from the pool balance and the paired D  quantity is burnt.&#x20;

<img src="../.gitbook/assets/file.excalidraw (14).svg" alt="" class="gitbook-drawing">



### Synth Units

Synth Collateral is stored as internal balance, but Synth holders are given units of ownership of the Synth Pool. This allows an interest rate to be applied. Synth holder’s claim on the collateral can be computed by assessing their ownership.&#x20;

All synth holders pay the same interest rate, which simply deletes a small amount of the total stored collateral balance. By slowly deleting the Synth Liability, Pool LPs accrue Pool Ownership, which offsets the Impermanent Loss experienced by presence of the Synths.&#x20;

<img src="../.gitbook/assets/file.excalidraw (15).svg" alt="" class="gitbook-drawing">

### Synth Leverage

Impermanent Loss/Gain is exacerbated by Synth Leverage. At 33% of the pool, Pool LPs experience 2x the IL if the price is unfavorable to them (the Asset is becoming more valuable than D). If the Asset becomes weaker, Pool LPs experience a 1.5x Impermanent Gain as they accrue extra Asset relative to D. Thus Pool LPs are inherently short the asset, whilst Synth holders are long the asset.&#x20;

<img src="../.gitbook/assets/file.excalidraw (16).svg" alt="" class="gitbook-drawing">

### Interest Rate Mechanism

Pool LPs earn all the fees and an interest rate from Synths. At 33% Synth Loading, Pool LPs are earning 1.5x their normal fee rate. The interest rate is coupled to the utilization of the Pool in Synth - set to a value to target the Synth Cap on a linear curve. This would likely be 0% at 0% Caps, \~5% at Max Caps, and extending to 100% at 100% Caps (the entire pool is underwriting the Synths, experienced after a 9x unfavorable price change).





<img src="../.gitbook/assets/file.excalidraw (17).svg" alt="" class="gitbook-drawing">



### Synths As Lending Collateral

Synths are only minted to store lending collateral. The loan is created by assessing 50% of the value in D Balance of the collateral, minting it in more D, and streaming on to the Debt Asset to the user. For example, if 10 WBTC are deposited for lending collateral, worth $600k, then $300k in D is minted and streamed out. A net gain of $300k is stored by the system. \


<img src="../.gitbook/assets/file.excalidraw (18).svg" alt="" class="gitbook-drawing">

### Liquidation

If a collateral position drops below 101% its debt value, then anyone can liquidate by deleting the position and claiming the 1% of stored Debt Value, swapped to any asset. If a position falls into “bad debt” (below 100%), then it means DECAVault holders will bear the position until it ever comes good. However since the collateral is a liability to Pool LPs, it is not necessarily a precipitous scenario, because Pool LPs are inherently short the asset they LP with.

<img src="../.gitbook/assets/file.excalidraw (19).svg" alt="" class="gitbook-drawing">

### Repaying Debt

At any stage a borrower can repay their debt to get back their claim on their Collateral. They stream in their original Debt Amount, which causes the streamed D to be burnt, and their collateral to be unlocked.&#x20;



<img src="../.gitbook/assets/file.excalidraw (20).svg" alt="" class="gitbook-drawing">

### Preventing Attacks

Since the max LTV a user can get is 50%, they will end up always with less debt than 50% of their deposit. This will prevent “bad debt” attacks, since the user is essentially just selling their tokens for a fee, which they can do anyway, if they get liquidated.&#x20;

\
\
