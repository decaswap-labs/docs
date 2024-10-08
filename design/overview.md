# Overview

### System Overview

There are 4 types of pools on the protocol; they are all single-sided:

1. All pools (AAVE, UNI, WIF)
2. Blue-chip pools (WBTC, WETH, USDT, USDC)
3. Global Pool (D)
4. DECA Pool (DECA)

<img src="../.gitbook/assets/file.excalidraw (5).svg" alt="" class="gitbook-drawing">

### All Pools

All pools are single-sided, with only external assets deposited. They are matched to an internal, arbitrary, unit of account referred to as “D”. Deposited liquidity is streamed in, which acquires the `D` asset thorugh arbitrage against all other pools. The reverse happens when liquidity is removed. Since D is matched to all pools, flows across pools simply move the D between, but D never leaves the contract.

<img src="../.gitbook/assets/file.excalidraw (6).svg" alt="" class="gitbook-drawing">

### Blue Chip Pools

Blue Chip Pools are a sub-set of Pools, with a certain privilege - `D` is instantly minted when assets are deposited instead of being purchased by arbitrage. This allows them to scale in depth rapidly. `D` is intantly-burnt when the asset liquidity is removed.&#x20;

<img src="../.gitbook/assets/file.excalidraw (7).svg" alt="" class="gitbook-drawing">

{% hint style="info" %}
&#x20;LPs cannot hold D, so when they deposit, they are taking up a short position of their asset versus {everything else} and are notionally long the volatility of that pool. Because of this, it makes sense to only pay the LP in USDC, and separate the principle from the yield.&#x20;
{% endhint %}

### Pool Creation

The Owner starts the system by creating a number of pools assigned to various tokens eg WBTC, WETH, USDT and USDC and DECA. The owner sets the balance of D minted as well as the required starting liquidity for each asset. Anyone can add the required liquidity. Once achieved, the pool starts trading. LPs are locked for 7 days.&#x20;

<img src="../.gitbook/assets/file.excalidraw (8).svg" alt="" class="gitbook-drawing">

### Global Pool (DPOOL)

There is a mechanism to become a “Global LP” which simply involves buying D and locking it in the DPOOL. DPOOL participants earn half of Global Income (from all pools) and experience an Impermanent Loss/Gain which is correlated to the performance of the system as a whole. It will be difficult to price DPOOL in units of anything other than USDC. D will be volatile.

<img src="../.gitbook/assets/file.excalidraw (4).svg" alt="" class="gitbook-drawing">

### DECA Pool (DECADAO)

The DECA token is fixed-supply and available for buy-sell in the market as an independent pool. DECA can attract a speculative premium and is a proxy for the yield of the system. DECA Pool LPs are the DECADAO. DECADAO earns 10% of System Income forever, claimed by members of the DAO. Anyone can buy DECA and lock to earn. DECA tokens can be held independently, and is the equity asset of the network. DECA has its own liquidity on the network. Users will buy DECA tokens to access future cash flows of the system. The DAO can propose any system parameter and action it after some time.&#x20;

### DECAMINT (RESERVE)

The DECA tokens in the DECAMINT can be nominated as a rewards token for the DECAPOOL and Pool LPs, and a stream rate can be set by DECADAO. The rewards can be claimed alongside USDC, as per the fee-claim logic.

<img src="../.gitbook/assets/file.excalidraw (21).svg" alt="" class="gitbook-drawing">
