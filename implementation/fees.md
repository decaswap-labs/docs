# Fees

#### Keeper Fees&#x20;

Every stream, pay the keeper 5BPS.

1. Keep in pool contract to minimise gas costs&#x20;
2. &#x20;Accrued in D per stream, swap to USDC, allocate to `msg.sender`

#### Liquidity Fees&#x20;

Every transferOut, retain 15BPS and pay to the System Income

1. Retain 45% to the Pool LPs
2. Swap 1/10 remaining to DECA Pool LPs
3. Swap remaining to USDC to allocate to Global LPs
