TickTest
========

Functions
---------

``tickSpacingToMaxLiquidityPerTick(int24 tickSpacing) → uint128``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``setTick(int24 tick, struct Tick.Info info)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``getFeeGrowthInside(int24 tickLower, int24 tickUpper, int24 tickCurrent, uint256 feeGrowthGlobal0X128, uint256 feeGrowthGlobal1X128) → uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``update(int24 tick, int24 tickCurrent, int128 liquidityDelta, uint256 feeGrowthGlobal0X128, uint256 feeGrowthGlobal1X128, uint160 secondsPerLiquidityCumulativeX128, int56 tickCumulative, uint32 time, bool upper, uint128 maxLiquidity) → bool flipped``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``clear(int24 tick)``
~~~~~~~~~~~~~~~~~~~~~

No description

``cross(int24 tick, uint256 feeGrowthGlobal0X128, uint256 feeGrowthGlobal1X128, uint160 secondsPerLiquidityCumulativeX128, int56 tickCumulative, uint32 time) → int128 liquidityNet``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description
