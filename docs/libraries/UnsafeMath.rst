UnsafeMath
==========

Contains methods that perform common math functions but do not do any
overflow or underflow checks

Functions
---------

``divRoundingUp(uint256 x, uint256 y) → uint256 z``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

division by 0 has unspecified behavior, and must be checked externally

Parameters:
^^^^^^^^^^^

-  ``x``: The dividend

-  ``y``: The divisor

Return Values:
^^^^^^^^^^^^^^

-  z The quotient, ceil(x / y)
