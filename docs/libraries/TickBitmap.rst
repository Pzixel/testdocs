TickBitmap
==========

Stores a packed mapping of tick index to its initialized state

The mapping uses int16 for keys since ticks are represented as int24 and
there are 256 (2^8) values per word.

Functions
---------

``flipTick(mapping(int16 => uint256) self, int24 tick, int24 tickSpacing)``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

Parameters:
^^^^^^^^^^^

-  ``self``: The mapping in which to flip the tick

-  ``tick``: The tick to flip

-  ``tickSpacing``: The spacing between usable ticks

``nextInitializedTickWithinOneWord(mapping(int16 => uint256) self, int24 tick, int24 tickSpacing, bool lte) → int24 next, bool initialized``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description

.. _parameters-1:

Parameters:
^^^^^^^^^^^

-  ``self``: The mapping in which to compute the next initialized tick

-  ``tick``: The starting tick

-  ``tickSpacing``: The spacing between usable ticks

-  ``lte``: Whether to search for the next initialized tick to the left
   (less than or equal to the starting tick)

Return Values:
^^^^^^^^^^^^^^

-  next The next initialized or uninitialized tick up to 256 ticks away
   from the current tick

-  initialized Whether the next tick is initialized, as the function
   only searches within up to 256 ticks
