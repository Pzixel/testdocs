Oracle
======

Provides price and liquidity data useful for a wide variety of system
designs

Instances of stored oracle data, “observations”, are collected in the
oracle array Every pool is initialized with an oracle array length of 1.
Anyone can pay the SSTOREs to increase the maximum length of the oracle
array. New slots will be added when the array is fully populated.
Observations are overwritten when the full length of the oracle array is
populated. The most recent observation is available, independent of the
length of the oracle array, by passing 0 to observe()

Functions
---------

``initialize(struct Oracle.Observation[65535] self, uint32 time) → uint16 cardinality, uint16 cardinalityNext``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description #### Parameters: - ``self``: The stored oracle array

-  ``time``: The time of the oracle initialization, via block.timestamp
   truncated to uint32

Return Values:
^^^^^^^^^^^^^^

-  cardinality The number of populated elements in the oracle array

-  cardinalityNext The new length of the oracle array, independent of
   population

``write(struct Oracle.Observation[65535] self, uint16 index, uint32 blockTimestamp, int24 tick, uint128 liquidity, uint16 cardinality, uint16 cardinalityNext) → uint16 indexUpdated, uint16 cardinalityUpdated``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Writable at most once per block. Index represents the most recently
written element. cardinality and index must be tracked externally. If
the index is at the end of the allowable array length (according to
cardinality), and the next cardinality is greater than the current one,
cardinality may be increased. This restriction is created to preserve
ordering.

Parameters:
^^^^^^^^^^^

-  ``self``: The stored oracle array

-  ``index``: The index of the observation that was most recently
   written to the observations array

-  ``blockTimestamp``: The timestamp of the new observation

-  ``tick``: The active tick at the time of the new observation

-  ``liquidity``: The total in-range liquidity at the time of the new
   observation

-  ``cardinality``: The number of populated elements in the oracle array

-  ``cardinalityNext``: The new length of the oracle array, independent
   of population

.. _return-values-1:

Return Values:
^^^^^^^^^^^^^^

-  indexUpdated The new index of the most recently written element in
   the oracle array

-  cardinalityUpdated The new cardinality of the oracle array

``grow(struct Oracle.Observation[65535] self, uint16 current, uint16 next) → uint16``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No description #### Parameters: - ``self``: The stored oracle array

-  ``current``: The current next cardinality of the oracle array

-  ``next``: The proposed next cardinality which will be populated in
   the oracle array

.. _return-values-2:

Return Values:
^^^^^^^^^^^^^^

-  next The next cardinality which will be populated in the oracle array

``observeSingle(struct Oracle.Observation[65535] self, uint32 time, uint32 secondsAgo, int24 tick, uint16 index, uint128 liquidity, uint16 cardinality) → int56 tickCumulative, uint160 secondsPerLiquidityCumulativeX128``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Reverts if an observation at or before the desired observation timestamp
does not exist. 0 may be passed as \`secondsAgo’ to return the current
cumulative values. If called with a timestamp falling between two
observations, returns the counterfactual accumulator values at exactly
the timestamp between the two observations.

.. _parameters-1:

Parameters:
^^^^^^^^^^^

-  ``self``: The stored oracle array

-  ``time``: The current block timestamp

-  ``secondsAgo``: The amount of time to look back, in seconds, at which
   point to return an observation

-  ``tick``: The current tick

-  ``index``: The index of the observation that was most recently
   written to the observations array

-  ``liquidity``: The current in-range pool liquidity

-  ``cardinality``: The number of populated elements in the oracle array

.. _return-values-3:

Return Values:
^^^^^^^^^^^^^^

-  tickCumulative The tick \* time elapsed since the pool was first
   initialized, as of ``secondsAgo``

-  secondsPerLiquidityCumulativeX128 The time elapsed / max(1,
   liquidity) since the pool was first initialized, as of ``secondsAgo``

``observe(struct Oracle.Observation[65535] self, uint32 time, uint32[] secondsAgos, int24 tick, uint16 index, uint128 liquidity, uint16 cardinality) → int56[] tickCumulatives, uint160[] secondsPerLiquidityCumulativeX128s``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Reverts if ``secondsAgos`` > oldest observation

.. _parameters-2:

Parameters:
^^^^^^^^^^^

-  ``self``: The stored oracle array

-  ``time``: The current block.timestamp

-  ``secondsAgos``: Each amount of time to look back, in seconds, at
   which point to return an observation

-  ``tick``: The current tick

-  ``index``: The index of the observation that was most recently
   written to the observations array

-  ``liquidity``: The current in-range pool liquidity

-  ``cardinality``: The number of populated elements in the oracle array

.. _return-values-4:

Return Values:
^^^^^^^^^^^^^^

-  tickCumulatives The tick \* time elapsed since the pool was first
   initialized, as of each ``secondsAgo``

-  secondsPerLiquidityCumulativeX128s The cumulative seconds / max(1,
   liquidity) since the pool was first initialized, as of each
   ``secondsAgo``
