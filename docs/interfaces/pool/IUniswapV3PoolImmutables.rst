IUniswapV3PoolImmutables
========================

These parameters are fixed for a pool forever, i.e., the methods will
always return the same values

Functions
---------

``factory() → address``
~~~~~~~~~~~~~~~~~~~~~~~

No description

Return Values:
^^^^^^^^^^^^^^

-  The contract address

``token0() → address``
~~~~~~~~~~~~~~~~~~~~~~

No description

.. _return-values-1:

Return Values:
^^^^^^^^^^^^^^

-  The token contract address

``token1() → address``
~~~~~~~~~~~~~~~~~~~~~~

No description

.. _return-values-2:

Return Values:
^^^^^^^^^^^^^^

-  The token contract address

``fee() → uint24``
~~~~~~~~~~~~~~~~~~

No description

.. _return-values-3:

Return Values:
^^^^^^^^^^^^^^

-  The fee

``tickSpacing() → int24``
~~~~~~~~~~~~~~~~~~~~~~~~~

Ticks can only be used at multiples of this value, minimum of 1 and
always positive e.g.: a tickSpacing of 3 means ticks can be initialized
every 3rd tick, i.e., …, -6, -3, 0, 3, 6, … This value is an int24 to
avoid casting even though it is always positive.

.. _return-values-4:

Return Values:
^^^^^^^^^^^^^^

-  The tick spacing

``maxLiquidityPerTick() → uint128``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This parameter is enforced per tick to prevent liquidity from
overflowing a uint128 at any point, and also prevents out-of-range
liquidity from being used to prevent adding in-range liquidity to a pool

.. _return-values-5:

Return Values:
^^^^^^^^^^^^^^

-  The max amount of liquidity per tick
