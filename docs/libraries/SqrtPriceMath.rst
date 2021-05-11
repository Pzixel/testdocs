SqrtPriceMath
=============

Contains the math that uses square root of price as a Q64.96 and
liquidity to compute deltas

Functions
---------

``getNextSqrtPriceFromAmount0RoundingUp(uint160 sqrtPX96, uint128 liquidity, uint256 amount, bool add) → uint160``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Always rounds up, because in the exact output case (increasing price) we
need to move the price at least far enough to get the desired output
amount, and in the exact input case (decreasing price) we need to move
the price less in order to not send too much output. The most precise
formula for this is liquidity \* sqrtPX96 / (liquidity +- amount \*
sqrtPX96), if this is impossible because of overflow, we calculate
liquidity / (liquidity / sqrtPX96 +- amount).

Parameters:
^^^^^^^^^^^

-  ``sqrtPX96``: The starting price, i.e. before accounting for the
   token0 delta

-  ``liquidity``: The amount of usable liquidity

-  ``amount``: How much of token0 to add or remove from virtual reserves

-  ``add``: Whether to add or remove the amount of token0

Return Values:
^^^^^^^^^^^^^^

-  The price after adding or removing amount, depending on add

``getNextSqrtPriceFromAmount1RoundingDown(uint160 sqrtPX96, uint128 liquidity, uint256 amount, bool add) → uint160``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Always rounds down, because in the exact output case (decreasing price)
we need to move the price at least far enough to get the desired output
amount, and in the exact input case (increasing price) we need to move
the price less in order to not send too much output. The formula we
compute is within <1 wei of the lossless version: sqrtPX96 +- amount /
liquidity

.. _parameters-1:

Parameters:
^^^^^^^^^^^

-  ``sqrtPX96``: The starting price, i.e., before accounting for the
   token1 delta

-  ``liquidity``: The amount of usable liquidity

-  ``amount``: How much of token1 to add, or remove, from virtual
   reserves

-  ``add``: Whether to add, or remove, the amount of token1

.. _return-values-1:

Return Values:
^^^^^^^^^^^^^^

-  The price after adding or removing ``amount``

``getNextSqrtPriceFromInput(uint160 sqrtPX96, uint128 liquidity, uint256 amountIn, bool zeroForOne) → uint160 sqrtQX96``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Throws if price or liquidity are 0, or if the next price is out of
bounds

.. _parameters-2:

Parameters:
^^^^^^^^^^^

-  ``sqrtPX96``: The starting price, i.e., before accounting for the
   input amount

-  ``liquidity``: The amount of usable liquidity

-  ``amountIn``: How much of token0, or token1, is being swapped in

-  ``zeroForOne``: Whether the amount in is token0 or token1

.. _return-values-2:

Return Values:
^^^^^^^^^^^^^^

-  sqrtQX96 The price after adding the input amount to token0 or token1

``getNextSqrtPriceFromOutput(uint160 sqrtPX96, uint128 liquidity, uint256 amountOut, bool zeroForOne) → uint160 sqrtQX96``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Throws if price or liquidity are 0 or the next price is out of bounds

.. _parameters-3:

Parameters:
^^^^^^^^^^^

-  ``sqrtPX96``: The starting price before accounting for the output
   amount

-  ``liquidity``: The amount of usable liquidity

-  ``amountOut``: How much of token0, or token1, is being swapped out

-  ``zeroForOne``: Whether the amount out is token0 or token1

.. _return-values-3:

Return Values:
^^^^^^^^^^^^^^

-  sqrtQX96 The price after removing the output amount of token0 or
   token1

``getAmount0Delta(uint160 sqrtRatioAX96, uint160 sqrtRatioBX96, uint128 liquidity, bool roundUp) → uint256 amount0``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Calculates liquidity / sqrt(lower) - liquidity / sqrt(upper),
i.e. liquidity \* (sqrt(upper) - sqrt(lower)) / (sqrt(upper) \*
sqrt(lower))

.. _parameters-4:

Parameters:
^^^^^^^^^^^

-  ``sqrtRatioAX96``: A sqrt price

-  ``sqrtRatioBX96``: Another sqrt price

-  ``liquidity``: The amount of usable liquidity

-  ``roundUp``: Whether to round the amount up or down

.. _return-values-4:

Return Values:
^^^^^^^^^^^^^^

-  amount0 Amount of token0 required to cover a position of size
   liquidity between the two passed prices

``getAmount1Delta(uint160 sqrtRatioAX96, uint160 sqrtRatioBX96, uint128 liquidity, bool roundUp) → uint256 amount1``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Calculates liquidity \* (sqrt(upper) - sqrt(lower))

.. _parameters-5:

Parameters:
^^^^^^^^^^^

-  ``sqrtRatioAX96``: A sqrt price

-  ``sqrtRatioBX96``: Another sqrt price

-  ``liquidity``: The amount of usable liquidity

-  ``roundUp``: Whether to round the amount up, or down

.. _return-values-5:

Return Values:
^^^^^^^^^^^^^^

-  amount1 Amount of token1 required to cover a position of size
   liquidity between the two passed prices

``getAmount0Delta(uint160 sqrtRatioAX96, uint160 sqrtRatioBX96, int128 liquidity) → int256 amount0``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

.. _parameters-6:

Parameters:
^^^^^^^^^^^

-  ``sqrtRatioAX96``: A sqrt price

-  ``sqrtRatioBX96``: Another sqrt price

-  ``liquidity``: The change in liquidity for which to compute the
   amount0 delta

.. _return-values-6:

Return Values:
^^^^^^^^^^^^^^

-  amount0 Amount of token0 corresponding to the passed liquidityDelta
   between the two prices

``getAmount1Delta(uint160 sqrtRatioAX96, uint160 sqrtRatioBX96, int128 liquidity) → int256 amount1``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

.. _parameters-7:

Parameters:
^^^^^^^^^^^

-  ``sqrtRatioAX96``: A sqrt price

-  ``sqrtRatioBX96``: Another sqrt price

-  ``liquidity``: The change in liquidity for which to compute the
   amount1 delta

.. _return-values-7:

Return Values:
^^^^^^^^^^^^^^

-  amount1 Amount of token1 corresponding to the passed liquidityDelta
   between the two prices
