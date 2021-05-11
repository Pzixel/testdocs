# IUniswapV3PoolActions


Contains pool methods that can be called by anyone


## Functions

### `initialize(uint160 sqrtPriceX96)`
Price is represented as a sqrt(amountToken1/amountToken0) Q64.96 value


#### Parameters:
- `sqrtPriceX96`: the initial sqrt price of the pool as a Q64.96

### `mint(address recipient, int24 tickLower, int24 tickUpper, uint128 amount, bytes data) → uint256 amount0, uint256 amount1`
The caller of this method receives a callback in the form of IUniswapV3MintCallback#uniswapV3MintCallback
in which they must pay any token0 or token1 owed for the liquidity. The amount of token0/token1 due depends
on tickLower, tickUpper, the amount of liquidity, and the current price.


#### Parameters:
- `recipient`: The address for which the liquidity will be created

- `tickLower`: The lower tick of the position in which to add liquidity

- `tickUpper`: The upper tick of the position in which to add liquidity

- `amount`: The amount of liquidity to mint

- `data`: Any data that should be passed through to the callback

#### Return Values:
- amount0 The amount of token0 that was paid to mint the given amount of liquidity. Matches the value in the callback

- amount1 The amount of token1 that was paid to mint the given amount of liquidity. Matches the value in the callback

### `collect(address recipient, int24 tickLower, int24 tickUpper, uint128 amount0Requested, uint128 amount1Requested) → uint128 amount0, uint128 amount1`
Does not recompute fees earned, which must be done either via mint or burn of any amount of liquidity.
Collect must be called by the position owner. To withdraw only token0 or only token1, amount0Requested or
amount1Requested may be set to zero. To withdraw all tokens owed, caller may pass any value greater than the
actual tokens owed, e.g. type(uint128).max. Tokens owed may be from accumulated swap fees or burned liquidity.


#### Parameters:
- `recipient`: The address which should receive the fees collected

- `tickLower`: The lower tick of the position for which to collect fees

- `tickUpper`: The upper tick of the position for which to collect fees

- `amount0Requested`: How much token0 should be withdrawn from the fees owed

- `amount1Requested`: How much token1 should be withdrawn from the fees owed

#### Return Values:
- amount0 The amount of fees collected in token0

- amount1 The amount of fees collected in token1

### `burn(int24 tickLower, int24 tickUpper, uint128 amount) → uint256 amount0, uint256 amount1`
Can be used to trigger a recalculation of fees owed to a position by calling with an amount of 0
Fees must be collected separately via a call to #collect


#### Parameters:
- `tickLower`: The lower tick of the position for which to burn liquidity

- `tickUpper`: The upper tick of the position for which to burn liquidity

- `amount`: How much liquidity to burn

#### Return Values:
- amount0 The amount of token0 sent to the recipient

- amount1 The amount of token1 sent to the recipient

### `swap(address recipient, bool zeroForOne, int256 amountSpecified, uint160 sqrtPriceLimitX96, bytes data) → int256 amount0, int256 amount1`
The caller of this method receives a callback in the form of IUniswapV3SwapCallback#uniswapV3SwapCallback


#### Parameters:
- `recipient`: The address to receive the output of the swap

- `zeroForOne`: The direction of the swap, true for token0 to token1, false for token1 to token0

- `amountSpecified`: The amount of the swap, which implicitly configures the swap as exact input (positive), or exact output (negative)

- `sqrtPriceLimitX96`: The Q64.96 sqrt price limit. If zero for one, the price cannot be less than this
value after the swap. If one for zero, the price cannot be greater than this value after the swap

- `data`: Any data to be passed through to the callback

#### Return Values:
- amount0 The delta of the balance of token0 of the pool, exact when negative, minimum when positive

- amount1 The delta of the balance of token1 of the pool, exact when negative, minimum when positive

### `flash(address recipient, uint256 amount0, uint256 amount1, bytes data)`
The caller of this method receives a callback in the form of IUniswapV3FlashCallback#uniswapV3FlashCallback
Can be used to donate underlying tokens pro-rata to currently in-range liquidity providers by calling
with 0 amount{0,1} and sending the donation amount(s) from the callback


#### Parameters:
- `recipient`: The address which will receive the token0 and token1 amounts

- `amount0`: The amount of token0 to send

- `amount1`: The amount of token1 to send

- `data`: Any data to be passed through to the callback

### `increaseObservationCardinalityNext(uint16 observationCardinalityNext)`
This method is no-op if the pool already has an observationCardinalityNext greater than or equal to
the input observationCardinalityNext.


#### Parameters:
- `observationCardinalityNext`: The desired minimum number of observations for the pool to store




