# Swaps

### Swaps

The continuous liquidity formula is used. All swaps are streaming swaps, which break them up into smaller streams to achieve the global Min Slippage, which are then queued into blocks. The Min Slippage for all pools is default 15BPS, but can be lowered by the DAO/Owner. The stream quantity is computed as per the smaller of the two pools a swap is being performed over.&#x20;

#### Swap

```
x = swapAmountIn
X = assetInDepth
y = swapAmountOut
X = assetOutDepth
y = x * Y / (x+X)
```

```
q = streamQuantity
x = swapAmountIn
S = globalMinSlippage
D = smallerPoolDepth
s = streamAmountIn

q = x / (S * D)
s = x / q
```

#### Asset <> Asset Swaps

```
Pool1: A:D1
Pool2: D2:B
a = swapIn
b = swapOut

d = a*D1/(a+A)
b = d*B/(d+D2)
b = (a*D1*B)/((d+D2)*(a+A))

A = A+a; D1 = D1-d; D2 = D2+d; B = B-b
```

### Stream Queue

All processing swaps live in Stream Queue that are executed one stream per block, and arranged per-pair (eg WBTC-WETH). When a user deposits a swap, they automatically bump everyone else’s streams as well, before hitting a sensible gas limit and exiting. If a deposit of a swap causes another user’s stream to finish, that user will naturally pay for the transferOut of that asset and the collection of fees.&#x20;

<img src="../.gitbook/assets/file.excalidraw (11).svg" alt="" class="gitbook-drawing">

If a user deposits a swap that finds another processing stream in the opposite direction, the two entire swaps are matched and one (or both) swaps will entirely be consumed. In this case, no D is moved at all, the swapAmounts are switched between the users and settled. One (or both) of the assets are transferred out and fees collected.&#x20;

<img src="../.gitbook/assets/file.excalidraw (12).svg" alt="" class="gitbook-drawing">

Every block a keeper-bot can bump the stream queue per pair, once only, and collect 5BPS on all streams. There can be unlimited swap-deposits by users though, they will simply skip stream-queue processing if already done.&#x20;

```
processPair(address asset, address asset, uint gasLimit)
```

### Limit Orders - Order Queue

Limit orders can be done as price-conditional swaps that sit in the Order Queue until meeting the correct price. If the price is achieved, they are pulled into the Stream Queue and consumed. Orders are inserted in a linked-list thus orders closest to the current price are found by searching and can easily be removed. An Order furtherest away from the current price will thus pay the highest gas cost to insert.&#x20;

Every time the Stream Queue per pair is bumped, the Order Queue last index is checked for execution. If it can be executed, it is moved into the Stream Queue and matched. Since the Stream Queue is processed first, the pool price will naturally move into a range that could match an Order, thus checking the Order Queue at the end is the correct choice.&#x20;

<img src="../.gitbook/assets/file.excalidraw (13).svg" alt="" class="gitbook-drawing">

### System Income

All swaps pay the System Income, which is assessed as 15BPS on finalised swaps. The fee is first converted to USDC then split three-ways: 10% to the DECADAO, then the remainder split equally between the DECAPOOL and Pool LPs. The USDC is sent to a single Income Contract which allows users to claim.

<img src="../.gitbook/assets/file.excalidraw (1) (1) (1).svg" alt="" class="gitbook-drawing">

\
\
