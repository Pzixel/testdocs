Tick
====

Contains functions for managing tick processes and relevant calculations

Functions
---------

``tickSpacingToMaxLiquidityPerTick(int24 tickSpacing) → uint128``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Executed within the pool constructor

Parameters:
^^^^^^^^^^^

-  ``tickSpacing``: The amount of required tick separation, realized in
   multiples of ``tickSpacing`` e.g., a tickSpacing of 3 requires ticks
   to be initialized every 3rd tick i.e., …, -6, -3, 0, 3, 6, …

Return Values:
^^^^^^^^^^^^^^

-  The max liquidity per tick

``getFeeGrowthInside(mapping(int24 => struct Tick.Info) self, int24 tickLower, int24 tickUpper, int24 tickCurrent, uint256 feeGrowthGlobal0X128, uint256 feeGrowthGlobal1X128) → uint256 feeGrowthInside0X128, uint256 feeGrowthInside1X128``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description #### Parameters: - ``self``: The mapping containing all
tick information for initialized ticks

-  ``tickLower``: The lower tick boundary of the position

-  ``tickUpper``: The upper tick boundary of the position

-  ``tickCurrent``: The current tick

-  ``feeGrowthGlobal0X128``: The all-time global fee growth, per unit of
   liquidity, in token0

-  ``feeGrowthGlobal1X128``: The all-time global fee growth, per unit of
   liquidity, in token1

.. _return-values-1:

Return Values:
^^^^^^^^^^^^^^

-  feeGrowthInside0X128 The all-time fee growth in token0, per unit of
   liquidity, inside the position’s tick boundaries

-  feeGrowthInside1X128 The all-time fee growth in token1, per unit of
   liquidity, inside the position’s tick boundaries

``update(mapping(int24 => struct Tick.Info) self, int24 tick, int24 tickCurrent, int128 liquidityDelta, uint256 feeGrowthGlobal0X128, uint256 feeGrowthGlobal1X128, uint160 secondsPerLiquidityCumulativeX128, int56 tickCumulative, uint32 time, bool upper, uint128 maxLiquidity) → bool flipped``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description #### Parameters: - ``self``: The mapping containing all
tick information for initialized ticks

-  ``tick``: The tick that will be updated

-  ``tickCurrent``: The current tick

-  ``liquidityDelta``: A new amount of liquidity to be added
   (subtracted) when tick is crossed from left to right (right to left)

-  ``feeGrowthGlobal0X128``: The all-time global fee growth, per unit of
   liquidity, in token0

-  ``feeGrowthGlobal1X128``: The all-time global fee growth, per unit of
   liquidity, in token1

-  ``secondsPerLiquidityCumulativeX128``: The all-time seconds per
   max(1, liquidity) of the pool

-  ``time``: The current block timestamp cast to a uint32

-  ``upper``: true for updating a position’s upper tick, or false for
   updating a position’s lower tick

-  ``maxLiquidity``: The maximum liquidity allocation for a single tick

.. _return-values-2:

Return Values:
^^^^^^^^^^^^^^

-  flipped Whether the tick was flipped from initialized to
   uninitialized, or vice versa

``clear(mapping(int24 => struct Tick.Info) self, int24 tick)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description #### Parameters: - ``self``: The mapping containing all
initialized tick information for initialized ticks

-  ``tick``: The tick that will be cleared

``cross(mapping(int24 => struct Tick.Info) self, int24 tick, uint256 feeGrowthGlobal0X128, uint256 feeGrowthGlobal1X128, uint160 secondsPerLiquidityCumulativeX128, int56 tickCumulative, uint32 time) → int128 liquidityNet``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description #### Parameters: - ``self``: The mapping containing all
tick information for initialized ticks

-  ``tick``: The destination tick of the transition

-  ``feeGrowthGlobal0X128``: The all-time global fee growth, per unit of
   liquidity, in token0

-  ``feeGrowthGlobal1X128``: The all-time global fee growth, per unit of
   liquidity, in token1

-  ``secondsPerLiquidityCumulativeX128``: The current seconds per
   liquidity

-  ``time``: The current block.timestamp

.. _return-values-3:

Return Values:
^^^^^^^^^^^^^^

-  liquidityNet The amount of liquidity added (subtracted) when tick is
   crossed from left to right (right to left)
