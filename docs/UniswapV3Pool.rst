UniswapV3Pool
=============

agasgasffnffnf

Functions
---------

``_blockTimestamp() → uint32``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Returns the block timestamp truncated to 32 bits, i.e. mod 2**32. This
method is overridden in tests.

``snapshotCumulativesInside(int24 tickLower, int24 tickUpper) → int56 tickCumulativeInside, uint160 secondsPerLiquidityInsideX128, uint32 secondsInside``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Snapshots must only be compared to other snapshots, taken over a period
for which a position existed. I.e., snapshots cannot be compared if a
position is not held for the entire period between when the first
snapshot is taken and the second snapshot is taken.

Parameters:
^^^^^^^^^^^

-  ``tickLower``: The lower tick of the range

-  ``tickUpper``: The upper tick of the range

Return Values:
^^^^^^^^^^^^^^

-  tickCumulativeInside The snapshot of the tick accumulator for the
   range

-  secondsPerLiquidityInsideX128 The snapshot of seconds per liquidity
   for the range

-  secondsInside The snapshot of seconds per liquidity for the range

``observe(uint32[] secondsAgos) → int56[] tickCumulatives, uint160[] secondsPerLiquidityCumulativeX128s``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To get a time weighted average tick or liquidity-in-range, you must call
this with two values, one representing the beginning of the period and
another for the end of the period. E.g., to get the last hour
time-weighted average tick, you must call it with secondsAgos = [3600,
0]. The time weighted average tick represents the geometric time
weighted average price of the pool, in log base sqrt(1.0001) of token1 /
token0. The TickMath library can be used to go from a tick value to a
ratio.

.. _parameters-1:

Parameters:
^^^^^^^^^^^

-  ``secondsAgos``: From how long ago each cumulative tick and liquidity
   value should be returned

.. _return-values-1:

Return Values:
^^^^^^^^^^^^^^

-  tickCumulatives Cumulative tick values as of each ``secondsAgos``
   from the current block timestamp

-  secondsPerLiquidityCumulativeX128s Cumulative seconds per
   liquidity-in-range value as of each ``secondsAgos`` from the current
   block timestamp

``increaseObservationCardinalityNext(uint16 observationCardinalityNext)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This method is no-op if the pool already has an
observationCardinalityNext greater than or equal to the input
observationCardinalityNext.

.. _parameters-2:

Parameters:
^^^^^^^^^^^

-  ``observationCardinalityNext``: The desired minimum number of
   observations for the pool to store

``initialize(uint160 sqrtPriceX96)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

not locked because it initializes unlocked #### Parameters: -
``sqrtPriceX96``: the initial sqrt price of the pool as a Q64.96

``mint(address recipient, int24 tickLower, int24 tickUpper, uint128 amount, bytes data) → uint256 amount0, uint256 amount1``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

noDelegateCall is applied indirectly via \_modifyPosition ####
Parameters: - ``recipient``: The address for which the liquidity will be
created

-  ``tickLower``: The lower tick of the position in which to add
   liquidity

-  ``tickUpper``: The upper tick of the position in which to add
   liquidity

-  ``amount``: The amount of liquidity to mint

-  ``data``: Any data that should be passed through to the callback

.. _return-values-2:

Return Values:
^^^^^^^^^^^^^^

-  amount0 The amount of token0 that was paid to mint the given amount
   of liquidity. Matches the value in the callback

-  amount1 The amount of token1 that was paid to mint the given amount
   of liquidity. Matches the value in the callback

``collect(address recipient, int24 tickLower, int24 tickUpper, uint128 amount0Requested, uint128 amount1Requested) → uint128 amount0, uint128 amount1``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Does not recompute fees earned, which must be done either via mint or
burn of any amount of liquidity. Collect must be called by the position
owner. To withdraw only token0 or only token1, amount0Requested or
amount1Requested may be set to zero. To withdraw all tokens owed, caller
may pass any value greater than the actual tokens owed,
e.g. type(uint128).max. Tokens owed may be from accumulated swap fees or
burned liquidity.

.. _parameters-3:

Parameters:
^^^^^^^^^^^

-  ``recipient``: The address which should receive the fees collected

-  ``tickLower``: The lower tick of the position for which to collect
   fees

-  ``tickUpper``: The upper tick of the position for which to collect
   fees

-  ``amount0Requested``: How much token0 should be withdrawn from the
   fees owed

-  ``amount1Requested``: How much token1 should be withdrawn from the
   fees owed

.. _return-values-3:

Return Values:
^^^^^^^^^^^^^^

-  amount0 The amount of fees collected in token0

-  amount1 The amount of fees collected in token1

``burn(int24 tickLower, int24 tickUpper, uint128 amount) → uint256 amount0, uint256 amount1``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

noDelegateCall is applied indirectly via \_modifyPosition ####
Parameters: - ``tickLower``: The lower tick of the position for which to
burn liquidity

-  ``tickUpper``: The upper tick of the position for which to burn
   liquidity

-  ``amount``: How much liquidity to burn

.. _return-values-4:

Return Values:
^^^^^^^^^^^^^^

-  amount0 The amount of token0 sent to the recipient

-  amount1 The amount of token1 sent to the recipient

``swap(address recipient, bool zeroForOne, int256 amountSpecified, uint160 sqrtPriceLimitX96, bytes data) → int256 amount0, int256 amount1``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The caller of this method receives a callback in the form of
IUniswapV3SwapCallback#uniswapV3SwapCallback

.. _parameters-4:

Parameters:
^^^^^^^^^^^

-  ``recipient``: The address to receive the output of the swap

-  ``zeroForOne``: The direction of the swap, true for token0 to token1,
   false for token1 to token0

-  ``amountSpecified``: The amount of the swap, which implicitly
   configures the swap as exact input (positive), or exact output
   (negative)

-  ``sqrtPriceLimitX96``: The Q64.96 sqrt price limit. If zero for one,
   the price cannot be less than this value after the swap. If one for
   zero, the price cannot be greater than this value after the swap

-  ``data``: Any data to be passed through to the callback

.. _return-values-5:

Return Values:
^^^^^^^^^^^^^^

-  amount0 The delta of the balance of token0 of the pool, exact when
   negative, minimum when positive

-  amount1 The delta of the balance of token1 of the pool, exact when
   negative, minimum when positive

``flash(address recipient, uint256 amount0, uint256 amount1, bytes data)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The caller of this method receives a callback in the form of
IUniswapV3FlashCallback#uniswapV3FlashCallback Can be used to donate
underlying tokens pro-rata to currently in-range liquidity providers by
calling with 0 amount{0,1} and sending the donation amount(s) from the
callback

.. _parameters-5:

Parameters:
^^^^^^^^^^^

-  ``recipient``: The address which will receive the token0 and token1
   amounts

-  ``amount0``: The amount of token0 to send

-  ``amount1``: The amount of token1 to send

-  ``data``: Any data to be passed through to the callback

``setFeeProtocol(uint8 feeProtocol0, uint8 feeProtocol1)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description #### Parameters: - ``feeProtocol0``: new protocol fee for
token0 of the pool

-  ``feeProtocol1``: new protocol fee for token1 of the pool

``collectProtocol(address recipient, uint128 amount0Requested, uint128 amount1Requested) → uint128 amount0, uint128 amount1``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description #### Parameters: - ``recipient``: The address to which
collected protocol fees should be sent

-  ``amount0Requested``: The maximum amount of token0 to send, can be 0
   to collect fees in only token1

-  ``amount1Requested``: The maximum amount of token1 to send, can be 0
   to collect fees in only token0

.. _return-values-6:

Return Values:
^^^^^^^^^^^^^^

-  amount0 The protocol fee collected in token0

-  amount1 The protocol fee collected in token1
