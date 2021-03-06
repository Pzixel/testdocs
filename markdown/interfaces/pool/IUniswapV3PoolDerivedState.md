# IUniswapV3PoolDerivedState


Contains view functions to provide information about the pool that is computed rather than stored on the
blockchain. The functions here may have variable gas costs.


## Functions

### `observe(uint32[] secondsAgos) → int56[] tickCumulatives, uint160[] secondsPerLiquidityCumulativeX128s`
To get a time weighted average tick or liquidity-in-range, you must call this with two values, one representing
the beginning of the period and another for the end of the period. E.g., to get the last hour time-weighted average tick,
you must call it with secondsAgos = [3600, 0].
The time weighted average tick represents the geometric time weighted average price of the pool, in
log base sqrt(1.0001) of token1 / token0. The TickMath library can be used to go from a tick value to a ratio.


#### Parameters:
- `secondsAgos`: From how long ago each cumulative tick and liquidity value should be returned

#### Return Values:
- tickCumulatives Cumulative tick values as of each `secondsAgos` from the current block timestamp

- secondsPerLiquidityCumulativeX128s Cumulative seconds per liquidity-in-range value as of each `secondsAgos` from the current block
timestamp

### `snapshotCumulativesInside(int24 tickLower, int24 tickUpper) → int56 tickCumulativeInside, uint160 secondsPerLiquidityInsideX128, uint32 secondsInside`
Snapshots must only be compared to other snapshots, taken over a period for which a position existed.
I.e., snapshots cannot be compared if a position is not held for the entire period between when the first
snapshot is taken and the second snapshot is taken.


#### Parameters:
- `tickLower`: The lower tick of the range

- `tickUpper`: The upper tick of the range

#### Return Values:
- tickCumulativeInside The snapshot of the tick accumulator for the range

- secondsPerLiquidityInsideX128 The snapshot of seconds per liquidity for the range

- secondsInside The snapshot of seconds per liquidity for the range




