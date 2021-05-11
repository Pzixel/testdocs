IUniswapV3PoolState
===================

These methods compose the pool’s state, and can change with any
frequency including multiple times per transaction

Functions
---------

``slot0() → uint160 sqrtPriceX96, int24 tick, uint16 observationIndex, uint16 observationCardinality, uint16 observationCardinalityNext, uint8 feeProtocol, bool unlocked``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

Return Values:
^^^^^^^^^^^^^^

-  sqrtPriceX96 The current price of the pool as a sqrt(token1/token0)
   Q64.96 value tick The current tick of the pool, i.e. according to the
   last tick transition that was run. This value may not always be equal
   to SqrtTickMath.getTickAtSqrtRatio(sqrtPriceX96) if the price is on a
   tick boundary. observationIndex The index of the last oracle
   observation that was written, observationCardinality The current
   maximum number of observations stored in the pool,
   observationCardinalityNext The next maximum number of observations,
   to be updated when the observation. feeProtocol The protocol fee for
   both tokens of the pool. Encoded as two 4 bit values, where the
   protocol fee of token1 is shifted 4 bits and the protocol fee of
   token0 is the lower 4 bits. Used as the denominator of a fraction of
   the swap fee, e.g. 4 means 1/4th of the swap fee. unlocked Whether
   the pool is currently locked to reentrancy

``feeGrowthGlobal0X128() → uint256``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This value can overflow the uint256

``feeGrowthGlobal1X128() → uint256``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This value can overflow the uint256

``protocolFees() → uint128 token0, uint128 token1``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Protocol fees will never exceed uint128 max in either token

``liquidity() → uint128``
~~~~~~~~~~~~~~~~~~~~~~~~~

This value has no relationship to the total liquidity across all ticks

``ticks(int24 tick) → uint128 liquidityGross, int128 liquidityNet, uint256 feeGrowthOutside0X128, uint256 feeGrowthOutside1X128, int56 tickCumulativeOutside, uint160 secondsPerLiquidityOutsideX128, uint32 secondsOutside, bool initialized``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

Parameters:
^^^^^^^^^^^

-  ``tick``: The tick to look up

.. _return-values-1:

Return Values:
^^^^^^^^^^^^^^

-  liquidityGross the total amount of position liquidity that uses the
   pool either as tick lower or tick upper, liquidityNet how much
   liquidity changes when the pool price crosses the tick,
   feeGrowthOutside0X128 the fee growth on the other side of the tick
   from the current tick in token0, feeGrowthOutside1X128 the fee growth
   on the other side of the tick from the current tick in token1,
   tickCumulativeOutside the cumulative tick value on the other side of
   the tick from the current tick secondsPerLiquidityOutsideX128 the
   seconds spent per liquidity on the other side of the tick from the
   current tick, secondsOutside the seconds spent on the other side of
   the tick from the current tick, initialized Set to true if the tick
   is initialized, i.e. liquidityGross is greater than 0, otherwise
   equal to false. Outside values can only be used if the tick is
   initialized, i.e. if liquidityGross is greater than 0. In addition,
   these values are only relative and must be used only in comparison to
   previous snapshots for a specific position.

``tickBitmap(int16 wordPosition) → uint256``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``positions(bytes32 key) → uint128 _liquidity, uint256 feeGrowthInside0LastX128, uint256 feeGrowthInside1LastX128, uint128 tokensOwed0, uint128 tokensOwed1``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

.. _parameters-1:

Parameters:
^^^^^^^^^^^

-  ``key``: The position’s key is a hash of a preimage composed by the
   owner, tickLower and tickUpper

.. _return-values-2:

Return Values:
^^^^^^^^^^^^^^

-  \_liquidity The amount of liquidity in the position, Returns
   feeGrowthInside0LastX128 fee growth of token0 inside the tick range
   as of the last mint/burn/poke, Returns feeGrowthInside1LastX128 fee
   growth of token1 inside the tick range as of the last mint/burn/poke,
   Returns tokensOwed0 the computed amount of token0 owed to the
   position as of the last mint/burn/poke, Returns tokensOwed1 the
   computed amount of token1 owed to the position as of the last
   mint/burn/poke

``observations(uint256 index) → uint32 blockTimestamp, int56 tickCumulative, uint160 secondsPerLiquidityCumulativeX128, bool initialized``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You most likely want to use #observe() instead of this method to get an
observation as of some amount of time ago, rather than at a specific
index in the array.

.. _parameters-2:

Parameters:
^^^^^^^^^^^

-  ``index``: The element of the observations array to fetch

.. _return-values-3:

Return Values:
^^^^^^^^^^^^^^

-  blockTimestamp The timestamp of the observation, Returns
   tickCumulative the tick multiplied by seconds elapsed for the life of
   the pool as of the observation timestamp, Returns
   secondsPerLiquidityCumulativeX128 the seconds per in range liquidity
   for the life of the pool as of the observation timestamp, Returns
   initialized whether the observation has been initialized and the
   values are safe to use
