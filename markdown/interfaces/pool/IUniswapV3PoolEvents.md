# IUniswapV3PoolEvents


Contains all events emitted by the pool





## Events

### `Initialize(uint160 sqrtPriceX96, int24 tick)`
Mint/Burn/Swap cannot be emitted by the pool before Initialize


#### Parameters:
- `sqrtPriceX96`: The initial sqrt price of the pool, as a Q64.96

- `tick`: The initial tick of the pool, i.e. log base 1.0001 of the starting price of the pool
### `Mint(address sender, address owner, int24 tickLower, int24 tickUpper, uint128 amount, uint256 amount0, uint256 amount1)`
No description

#### Parameters:
- `sender`: The address that minted the liquidity

- `owner`: The owner of the position and recipient of any minted liquidity

- `tickLower`: The lower tick of the position

- `tickUpper`: The upper tick of the position

- `amount`: The amount of liquidity minted to the position range

- `amount0`: How much token0 was required for the minted liquidity

- `amount1`: How much token1 was required for the minted liquidity
### `Collect(address owner, address recipient, int24 tickLower, int24 tickUpper, uint128 amount0, uint128 amount1)`
Collect events may be emitted with zero amount0 and amount1 when the caller chooses not to collect fees


#### Parameters:
- `owner`: The owner of the position for which fees are collected

- `tickLower`: The lower tick of the position

- `tickUpper`: The upper tick of the position

- `amount0`: The amount of token0 fees collected

- `amount1`: The amount of token1 fees collected
### `Burn(address owner, int24 tickLower, int24 tickUpper, uint128 amount, uint256 amount0, uint256 amount1)`
Does not withdraw any fees earned by the liquidity position, which must be withdrawn via #collect


#### Parameters:
- `owner`: The owner of the position for which liquidity is removed

- `tickLower`: The lower tick of the position

- `tickUpper`: The upper tick of the position

- `amount`: The amount of liquidity to remove

- `amount0`: The amount of token0 withdrawn

- `amount1`: The amount of token1 withdrawn
### `Swap(address sender, address recipient, int256 amount0, int256 amount1, uint160 sqrtPriceX96, int24 tick)`
No description

#### Parameters:
- `sender`: The address that initiated the swap call, and that received the callback

- `recipient`: The address that received the output of the swap

- `amount0`: The delta of the token0 balance of the pool

- `amount1`: The delta of the token1 balance of the pool

- `sqrtPriceX96`: The sqrt(price) of the pool after the swap, as a Q64.96

- `tick`: The log base 1.0001 of price of the pool after the swap
### `Flash(address sender, address recipient, uint256 amount0, uint256 amount1, uint256 paid0, uint256 paid1)`
No description

#### Parameters:
- `sender`: The address that initiated the swap call, and that received the callback

- `recipient`: The address that received the tokens from flash

- `amount0`: The amount of token0 that was flashed

- `amount1`: The amount of token1 that was flashed

- `paid0`: The amount of token0 paid for the flash, which can exceed the amount0 plus the fee

- `paid1`: The amount of token1 paid for the flash, which can exceed the amount1 plus the fee
### `IncreaseObservationCardinalityNext(uint16 observationCardinalityNextOld, uint16 observationCardinalityNextNew)`
observationCardinalityNext is not the observation cardinality until an observation is written at the index
just before a mint/swap/burn.


#### Parameters:
- `observationCardinalityNextOld`: The previous value of the next observation cardinality

- `observationCardinalityNextNew`: The updated value of the next observation cardinality
### `SetFeeProtocol(uint8 feeProtocol0Old, uint8 feeProtocol1Old, uint8 feeProtocol0New, uint8 feeProtocol1New)`
No description

#### Parameters:
- `feeProtocol0Old`: The previous value of the token0 protocol fee

- `feeProtocol1Old`: The previous value of the token1 protocol fee

- `feeProtocol0New`: The updated value of the token0 protocol fee

- `feeProtocol1New`: The updated value of the token1 protocol fee
### `CollectProtocol(address sender, address recipient, uint128 amount0, uint128 amount1)`
No description

#### Parameters:
- `sender`: The address that collects the protocol fees

- `recipient`: The address that receives the collected protocol fees

- `amount0`: The amount of token0 protocol fees that is withdrawn

- `amount0`: The amount of token1 protocol fees that is withdrawn
