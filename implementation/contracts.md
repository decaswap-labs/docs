# Contracts

###

<img src="../.gitbook/assets/file.excalidraw (6).svg" alt="" class="gitbook-drawing">

### Router Contract

The global router contract will provide the interface to swap between assets, add/remove liquidity and borrow assets. It will also provide the DECAVault and DECADAO interface. It is not intended to be regularly upgraded and will point to the Logic Contract.&#x20;

### Pool Contract

All pool assets should be held in a single contract:

* D Liquidity Units
* Pool Ownership Units
* Pool Synthetic Units
* User Synthetic Collateral
* User Debt Units
* Pool Assets&#x20;
* Stream Queue and Order Queue
* Accumulated Fees for Keepers and System Income

### Logic Contract

All swap, limit orders, add liquidity, lending Interest and System Income logic is handled in an asset-less Logic Contract that can be upgraded by the Owner regularly. In this way, the system can start with basic swaps, then slowly add limit orders, streaming and finally lending.&#x20;

This includes logic for minting/burning Units, Collateral, and Debt, but the state for those units are stored in the Pool Contract.&#x20;

### Income Contract

Fees & Income are transferred to a separate contract. The contract looks back at either the Pool Contract or the DECADAO Contract to determine respective ownership then allows members to claim pro-rata with the `rewardDebt` MasterChef method.&#x20;

### DECAMINT (Rewards) Contract

A separate DECAMint contract holds the DECAMint supply and streams out to the Income Contract. This contract will only hold DECA tokens. The owner can update reward streams and pool's whitelisted to collect.&#x20;

### Utils Contract

A separate Utils Contract will hold math and other utility features that should not need regular upgrading.&#x20;

### DECADAO

Locked DECADAO tokens are held in the DAO Contract, as well as the logic for voting and setting system parameters. Initially an Owner will manage global parameters and addresses for the Router, Logic and Utils contracts, but overtime this will be transferred to this DAO contract.
