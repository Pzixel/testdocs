The Uniswap V3 Factory facilitates creation of Uniswap V3 pools and
control over the protocol fees

Functions:
==========

Function ``owner() → address``
------------------------------

Can be changed by the current owner via setOwner

Return Values:
~~~~~~~~~~~~~~

-  The address of the factory owner

Function ``feeAmountTickSpacing(uint24 fee) → int24``
-----------------------------------------------------

A fee amount can never be removed, so this value should be hard coded or
cached in the calling context

Parameters:
~~~~~~~~~~~

-  ``fee``: The enabled fee, denominated in hundredths of a bip. Returns
   0 in case of unenabled fee

.. _return-values-1:

Return Values:
~~~~~~~~~~~~~~

-  The tick spacing

Function ``getPool(address tokenA, address tokenB, uint24 fee) → address pool``
-------------------------------------------------------------------------------

tokenA and tokenB may be passed in either token0/token1 or token1/token0
order

.. _parameters-1:

Parameters:
~~~~~~~~~~~

-  ``tokenA``: The contract address of either token0 or token1

-  ``tokenB``: The contract address of the other token

-  ``fee``: The fee collected upon every swap in the pool, denominated
   in hundredths of a bip

.. _return-values-2:

Return Values:
~~~~~~~~~~~~~~

-  pool The pool address

Function ``createPool(address tokenA, address tokenB, uint24 fee) → address pool``
----------------------------------------------------------------------------------

tokenA and tokenB may be passed in either order: token0/token1 or
token1/token0. tickSpacing is retrieved

from the fee. The call will revert if the pool already exists, the fee
is invalid, or the token arguments

are invalid.

.. _parameters-2:

Parameters:
~~~~~~~~~~~

-  ``tokenA``: One of the two tokens in the desired pool

-  ``tokenB``: The other of the two tokens in the desired pool

-  ``fee``: The desired fee for the pool

.. _return-values-3:

Return Values:
~~~~~~~~~~~~~~

-  pool The address of the newly created pool

Function ``setOwner(address _owner)``
-------------------------------------

Must be called by the current owner

.. _parameters-3:

Parameters:
~~~~~~~~~~~

-  ``_owner``: The new owner of the factory

Function ``enableFeeAmount(uint24 fee, int24 tickSpacing)``
-----------------------------------------------------------

Fee amounts may never be removed once enabled

.. _parameters-4:

Parameters:
~~~~~~~~~~~

-  ``fee``: The fee amount to enable, denominated in hundredths of a bip
   (i.e. 1e-6)

-  ``tickSpacing``: The spacing between ticks to be enforced for all
   pools created with the given fee amount

Events:
=======

.. _IUniswapV3Factory-OwnerChanged-address-address-:

Event ``OwnerChanged(address oldOwner, address newOwner)``
==========================================================

No description

.. _parameters-5:

Parameters:
-----------

-  ``oldOwner``: The owner before the owner was changed

-  ``newOwner``: The owner after the owner was changed

.. _IUniswapV3Factory-PoolCreated-address-address-uint24-int24-address-:

Event ``PoolCreated(address token0, address token1, uint24 fee, int24 tickSpacing, address pool)``
==================================================================================================

No description

.. _parameters-6:

Parameters:
-----------

-  ``token0``: The first token of the pool by address sort order

-  ``token1``: The second token of the pool by address sort order

-  ``fee``: The fee collected upon every swap in the pool, denominated
   in hundredths of a bip

-  ``tickSpacing``: The minimum number of ticks between initialized
   ticks

-  ``pool``: The address of the created pool

.. _IUniswapV3Factory-FeeAmountEnabled-uint24-int24-:

Event ``FeeAmountEnabled(uint24 fee, int24 tickSpacing)``
=========================================================

No description

.. _parameters-7:

Parameters:
-----------

-  ``fee``: The enabled fee, denominated in hundredths of a bip

-  ``tickSpacing``: The minimum number of ticks between initialized
   ticks for pools created with the given fee
