BitMath
=======

This library provides functionality for computing bit properties of an
unsigned integer

Functions
---------

``mostSignificantBit(uint256 x) → uint8 r``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The function satisfies the property: x >= 2\ **mostSignificantBit(x) and
x < 2**\ (mostSignificantBit(x)+1)

Parameters:
^^^^^^^^^^^

-  ``x``: the value for which to compute the most significant bit, must
   be greater than 0

Return Values:
^^^^^^^^^^^^^^

-  r the index of the most significant bit

``leastSignificantBit(uint256 x) → uint8 r``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The function satisfies the property: (x & 2\ **leastSignificantBit(x))
!= 0 and (x & (2**\ (leastSignificantBit(x)) - 1)) == 0)

.. _parameters-1:

Parameters:
^^^^^^^^^^^

-  ``x``: the value for which to compute the least significant bit, must
   be greater than 0

.. _return-values-1:

Return Values:
^^^^^^^^^^^^^^

-  r the index of the least significant bit
