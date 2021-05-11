TestUniswapV3Callee
===================

Functions
---------

``swapExact0For1(address pool, uint256 amount0In, address recipient, uint160 sqrtPriceLimitX96)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``swap0ForExact1(address pool, uint256 amount1Out, address recipient, uint160 sqrtPriceLimitX96)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``swapExact1For0(address pool, uint256 amount1In, address recipient, uint160 sqrtPriceLimitX96)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``swap1ForExact0(address pool, uint256 amount0Out, address recipient, uint160 sqrtPriceLimitX96)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``swapToLowerSqrtPrice(address pool, uint160 sqrtPriceX96, address recipient)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``swapToHigherSqrtPrice(address pool, uint160 sqrtPriceX96, address recipient)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``uniswapV3SwapCallback(int256 amount0Delta, int256 amount1Delta, bytes data)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``mint(address pool, address recipient, int24 tickLower, int24 tickUpper, uint128 amount)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``uniswapV3MintCallback(uint256 amount0Owed, uint256 amount1Owed, bytes data)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``flash(address pool, address recipient, uint256 amount0, uint256 amount1, uint256 pay0, uint256 pay1)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

``uniswapV3FlashCallback(uint256 fee0, uint256 fee1, bytes data)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

Events
------

``SwapCallback(int256 amount0Delta, int256 amount1Delta)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description ###
``MintCallback(uint256 amount0Owed, uint256 amount1Owed)`` No
description ### ``FlashCallback(uint256 fee0, uint256 fee1)`` No
description
