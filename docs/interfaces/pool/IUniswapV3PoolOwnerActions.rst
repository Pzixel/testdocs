IUniswapV3PoolOwnerActions
==========================

Contains pool methods that may only be called by the factory owner

Functions
---------

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

Return Values:
^^^^^^^^^^^^^^

-  amount0 The protocol fee collected in token0

-  amount1 The protocol fee collected in token1
