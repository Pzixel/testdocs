TransferHelper
==============

Contains helper methods for interacting with ERC20 tokens that do not
consistently return true/false

Functions
---------

``safeTransfer(address token, address to, uint256 value)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Calls transfer on token contract, errors with TF if transfer fails

Parameters:
^^^^^^^^^^^

-  ``token``: The contract address of the token which will be
   transferred

-  ``to``: The recipient of the transfer

-  ``value``: The value of the transfer
