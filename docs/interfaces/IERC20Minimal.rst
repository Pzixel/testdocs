IERC20Minimal
=============

Contains a subset of the full ERC20 interface that is used in Uniswap V3

Functions
---------

``balanceOf(address account) → uint256``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

Parameters:
^^^^^^^^^^^

-  ``account``: The account for which to look up the number of tokens it
   has, i.e. its balance

Return Values:
^^^^^^^^^^^^^^

-  The number of tokens held by the account

``transfer(address recipient, uint256 amount) → bool``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

.. _parameters-1:

Parameters:
^^^^^^^^^^^

-  ``recipient``: The account that will receive the amount transferred

-  ``amount``: The number of tokens to send from the sender to the
   recipient

.. _return-values-1:

Return Values:
^^^^^^^^^^^^^^

-  Returns true for a successful transfer, false for an unsuccessful
   transfer

``allowance(address owner, address spender) → uint256``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

.. _parameters-2:

Parameters:
^^^^^^^^^^^

-  ``owner``: The account of the token owner

-  ``spender``: The account of the token spender

.. _return-values-2:

Return Values:
^^^^^^^^^^^^^^

-  The current allowance granted by ``owner`` to ``spender``

``approve(address spender, uint256 amount) → bool``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

.. _parameters-3:

Parameters:
^^^^^^^^^^^

-  ``spender``: The account which will be allowed to spend a given
   amount of the owners tokens

-  ``amount``: The amount of tokens allowed to be used by ``spender``

.. _return-values-3:

Return Values:
^^^^^^^^^^^^^^

-  Returns true for a successful approval, false for unsuccessful

``transferFrom(address sender, address recipient, uint256 amount) → bool``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

.. _parameters-4:

Parameters:
^^^^^^^^^^^

-  ``sender``: The account from which the transfer will be initiated

-  ``recipient``: The recipient of the transfer

-  ``amount``: The amount of the transfer

.. _return-values-4:

Return Values:
^^^^^^^^^^^^^^

-  Returns true for a successful transfer, false for unsuccessful

Events
------

``Transfer(address from, address to, uint256 value)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

.. _parameters-5:

Parameters:
^^^^^^^^^^^

-  ``from``: The account from which the tokens were sent, i.e. the
   balance decreased

-  ``to``: The account to which the tokens were sent, i.e. the balance
   increased

-  ``value``: The amount of tokens that were transferred ###
   ``Approval(address owner, address spender, uint256 value)`` No
   description

.. _parameters-6:

Parameters:
^^^^^^^^^^^

-  ``owner``: The account that approved spending of its tokens

-  ``spender``: The account for which the spending allowance was
   modified

-  ``value``: The new allowance from the owner to the spender
