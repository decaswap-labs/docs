# Swap Processing

## Swap

### Swap Deposit

Managed as a linked list for easy insertion/removal. &#x20;

```
mapping(address => mapping(address => uint)) public lastStreamedIndexForPair;
```

```
swap(address tokenIn, address tokenOut, uint amountIn) public
```

```

struct Swap {
        uint swapID;
        address swapInAsset;
        uint swapInAmountRemaining;
        uint streamsRemaining;
        address swapOutAsset;
        uint swapOutAmountDone;
        bool processing;
        uint priceToStartStreaming;
        uint lastStreamedBlock;
    }
```

1. A user deposits a swap in a direction, add to end of Stream Queue
2. Start Stream Queue first from the last processed index
3. Stream the Queue, accumulate fees in outgoing asset, then exit at gasLimit, update the last processed index&#x20;
4. Check Order Queue, if valid price, then add to Opposite Stream Queue
5. Check Opposite Swaps, if any, Match then Settle with User's SwapID
6. Transfer out Assets, send Fees to System

```
processStream(address tokenIn, address tokenOut, uint gasLimit=100,000)
=> start at lastStreamedIndexForPair
=> stream the queue, exit at gasLimit
=> fees accumulated in outgoing asset for msg.sender swapID

checkOrderQueue(address tokenOut, address tokenIn)
=> if found move to SwapQueue

checkSwapQueue(address tokenOut, address tokenIn) //opposite direction
=> if found, match, settle

processTransferOut(uint swapID)
=> send out for user, pay fees
```

###



<img src="../.gitbook/assets/file.excalidraw (22).svg" alt="" class="gitbook-drawing">

### Order Deposit

Uses a linked list.&#x20;

1. A user deposits in a direction, with price
2. If current price valid, then process as per Swap Deposit
3. If not valid, search Order Queue, looking for correct price to insert.&#x20;
4. Insert.&#x20;

```
swap(address tokenIn, address tokenOut, uint amountIn, uint priceToStartStreaming) public
```

```
checkPrice(uint priceToStartStreaming)
=> if valid, insert into Swap Queue
=> processStream()

insertOrder(address tokenIn, address tokenOut, uint priceToStartStreaming)
=> insert order at correct index
```

### Swap Cancel

```
cancel(uint swapID) public
=> return any assets to sender (could be pending or processing)
```

### Keeper Bot - Swap Queue

1. Nominates pair, direction, gas limit
2. Fees are 5BPS on all streams, accumulated in outgoing asset for the bot
3. Will do Stream Queue first, and also do the Order Queue.&#x20;



<img src="../.gitbook/assets/file.excalidraw.svg" alt="" class="gitbook-drawing">

