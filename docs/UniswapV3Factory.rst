UniswapV3Factory
================

Deploys Uniswap V3 pools and manages ownership and control over pool
protocol fees

Functions
---------

``createPool(address tokenA, address tokenB, uint24 fee) → address pool``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

tokenA and tokenB may be passed in either order: token0/token1 or
token1/token0. tickSpacing is retrieved from the fee. The call will
revert if the pool already exists, the fee is invalid, or the token
arguments are invalid.

Parameters:
^^^^^^^^^^^

-  ``tokenA``: One of the two tokens in the desired pool

-  ``tokenB``: The other of the two tokens in the desired pool

-  ``fee``: The desired fee for the pool

Return Values:
^^^^^^^^^^^^^^

-  pool The address of the newly created pool

``setOwner(address _owner)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Must be called by the current owner

.. _parameters-1:

Parameters:
^^^^^^^^^^^

-  ``_owner``: The new owner of the factory

``enableFeeAmount(uint24 fee, int24 tickSpacing)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Fee amounts may never be removed once enabled

.. _parameters-2:

Parameters:
^^^^^^^^^^^

-  ``fee``: The fee amount to enable, denominated in hundredths of a bip
   (i.e. 1e-6)

-  ``tickSpacing``: The spacing between ticks to be enforced for all
   pools created with the given fee amount
