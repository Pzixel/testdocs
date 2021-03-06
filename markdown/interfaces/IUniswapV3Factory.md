# IUniswapV3Factory


The Uniswap V3 Factory facilitates creation of Uniswap V3 pools and control over the protocol fees


## Functions

### `owner() → address`
Can be changed by the current owner via setOwner


#### Return Values:
- The address of the factory owner

### `feeAmountTickSpacing(uint24 fee) → int24`
A fee amount can never be removed, so this value should be hard coded or cached in the calling context


#### Parameters:
- `fee`: The enabled fee, denominated in hundredths of a bip. Returns 0 in case of unenabled fee

#### Return Values:
- The tick spacing

### `getPool(address tokenA, address tokenB, uint24 fee) → address pool`
tokenA and tokenB may be passed in either token0/token1 or token1/token0 order


#### Parameters:
- `tokenA`: The contract address of either token0 or token1

- `tokenB`: The contract address of the other token

- `fee`: The fee collected upon every swap in the pool, denominated in hundredths of a bip

#### Return Values:
- pool The pool address

### `createPool(address tokenA, address tokenB, uint24 fee) → address pool`
tokenA and tokenB may be passed in either order: token0/token1 or token1/token0. tickSpacing is retrieved
from the fee. The call will revert if the pool already exists, the fee is invalid, or the token arguments
are invalid.


#### Parameters:
- `tokenA`: One of the two tokens in the desired pool

- `tokenB`: The other of the two tokens in the desired pool

- `fee`: The desired fee for the pool

#### Return Values:
- pool The address of the newly created pool

### `setOwner(address _owner)`
Must be called by the current owner


#### Parameters:
- `_owner`: The new owner of the factory

### `enableFeeAmount(uint24 fee, int24 tickSpacing)`
Fee amounts may never be removed once enabled


#### Parameters:
- `fee`: The fee amount to enable, denominated in hundredths of a bip (i.e. 1e-6)

- `tickSpacing`: The spacing between ticks to be enforced for all pools created with the given fee amount



## Events

### `OwnerChanged(address oldOwner, address newOwner)`
No description

#### Parameters:
- `oldOwner`: The owner before the owner was changed

- `newOwner`: The owner after the owner was changed
### `PoolCreated(address token0, address token1, uint24 fee, int24 tickSpacing, address pool)`
No description

#### Parameters:
- `token0`: The first token of the pool by address sort order

- `token1`: The second token of the pool by address sort order

- `fee`: The fee collected upon every swap in the pool, denominated in hundredths of a bip

- `tickSpacing`: The minimum number of ticks between initialized ticks

- `pool`: The address of the created pool
### `FeeAmountEnabled(uint24 fee, int24 tickSpacing)`
No description

#### Parameters:
- `fee`: The enabled fee, denominated in hundredths of a bip

- `tickSpacing`: The minimum number of ticks between initialized ticks for pools created with the given fee
