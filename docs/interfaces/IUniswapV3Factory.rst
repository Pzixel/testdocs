Functions:
==========

-  :ref:`owner()  <IUniswapV3Factory-owner-->`
-  :ref:`feeAmountTickSpacing(uint24
   fee)  <IUniswapV3Factory-feeAmountTickSpacing-uint24->`
-  :ref:`getPool(address tokenA, address tokenB, uint24
   fee)  <IUniswapV3Factory-getPool-address-address-uint24->`
-  :ref:`createPool(address tokenA, address tokenB, uint24
   fee)  <IUniswapV3Factory-createPool-address-address-uint24->`
-  :ref:`setOwner(address \_owner)  <IUniswapV3Factory-setOwner-address->`
-  :ref:`enableFeeAmount(uint24 fee, int24
   tickSpacing)  <IUniswapV3Factory-enableFeeAmount-uint24-int24->`

Events:
=======

-  :ref:`OwnerChanged(address oldOwner, address
   newOwner)  <IUniswapV3Factory-OwnerChanged-address-address->`
-  :ref:`PoolCreated(address token0, address token1, uint24 fee, int24
   tickSpacing, address
   pool)  <IUniswapV3Factory-PoolCreated-address-address-uint24-int24-address->`
-  :ref:`FeeAmountEnabled(uint24 fee, int24
   tickSpacing)  <IUniswapV3Factory-FeeAmountEnabled-uint24-int24->`

.. _IUniswapV3Factory-owner--:

Function ``owner() → address``
==============================

Can be changed by the current owner via setOwner

Return Values:
--------------

-  The address of the factory owner # Function
   ``feeAmountTickSpacing(uint24 fee) → int24``
   {#IUniswapV3Factory-feeAmountTickSpacing-uint24-} A fee amount can
   never be removed, so this value should be hard coded or cached in the
   calling context

Parameters:
-----------

-  ``fee``: The enabled fee, denominated in hundredths of a bip. Returns
   0 in case of unenabled fee

.. _return-values-1:

Return Values:
--------------

-  The tick spacing # Function
   ``getPool(address tokenA, address tokenB, uint24 fee) → address pool``
   {#IUniswapV3Factory-getPool-address-address-uint24-} tokenA and
   tokenB may be passed in either token0/token1 or token1/token0 order

.. _parameters-1:

Parameters:
-----------

-  ``tokenA``: The contract address of either token0 or token1

-  ``tokenB``: The contract address of the other token

-  ``fee``: The fee collected upon every swap in the pool, denominated
   in hundredths of a bip

.. _return-values-2:

Return Values:
--------------

-  pool The pool address # Function
   ``createPool(address tokenA, address tokenB, uint24 fee) → address pool``
   {#IUniswapV3Factory-createPool-address-address-uint24-} tokenA and
   tokenB may be passed in either order: token0/token1 or token1/token0.
   tickSpacing is retrieved from the fee. The call will revert if the
   pool already exists, the fee is invalid, or the token arguments are
   invalid.

.. _parameters-2:

Parameters:
-----------

-  ``tokenA``: One of the two tokens in the desired pool

-  ``tokenB``: The other of the two tokens in the desired pool

-  ``fee``: The desired fee for the pool

.. _return-values-3:

Return Values:
--------------

-  pool The address of the newly created pool # Function
   ``setOwner(address _owner)`` {#IUniswapV3Factory-setOwner-address-}
   Must be called by the current owner

.. _parameters-3:

Parameters:
-----------

-  ``_owner``: The new owner of the factory # Function
   ``enableFeeAmount(uint24 fee, int24 tickSpacing)``
   {#IUniswapV3Factory-enableFeeAmount-uint24-int24-} Fee amounts may
   never be removed once enabled

.. _parameters-4:

Parameters:
-----------

-  ``fee``: The fee amount to enable, denominated in hundredths of a bip
   (i.e. 1e-6)

-  ``tickSpacing``: The spacing between ticks to be enforced for all
   pools created with the given fee amount

.. _IUniswapV3Factory-OwnerChanged-address-address-:

Event ``OwnerChanged(address oldOwner, address newOwner)``
==========================================================

No description ## Parameters: - ``oldOwner``: The owner before the owner
was changed

-  ``newOwner``: The owner after the owner was changed # Event
   ``PoolCreated(address token0, address token1, uint24 fee, int24 tickSpacing, address pool)``
   {#IUniswapV3Factory-PoolCreated-address-address-uint24-int24-address-}
   No description ## Parameters:

-  ``token0``: The first token of the pool by address sort order

-  ``token1``: The second token of the pool by address sort order

-  ``fee``: The fee collected upon every swap in the pool, denominated
   in hundredths of a bip

-  ``tickSpacing``: The minimum number of ticks between initialized
   ticks

-  ``pool``: The address of the created pool # Event
   ``FeeAmountEnabled(uint24 fee, int24 tickSpacing)``
   {#IUniswapV3Factory-FeeAmountEnabled-uint24-int24-} No description ##
   Parameters:

-  ``fee``: The enabled fee, denominated in hundredths of a bip

-  ``tickSpacing``: The minimum number of ticks between initialized
   ticks for pools created with the given fee
