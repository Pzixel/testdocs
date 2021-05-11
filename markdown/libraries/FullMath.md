# FullMath


Facilitates multiplication and division that can have overflow of an intermediate value without any loss of precision

Handles "phantom overflow" i.e., allows multiplication and division where an intermediate value overflows 256 bits

## Functions

### `mulDiv(uint256 a, uint256 b, uint256 denominator) → uint256 result`
Credit to Remco Bloemen under MIT license https://xn--2-umb.com/21/muldiv

#### Parameters:
- `a`: The multiplicand

- `b`: The multiplier

- `denominator`: The divisor

#### Return Values:
- result The 256-bit result


### `mulDivRoundingUp(uint256 a, uint256 b, uint256 denominator) → uint256 result`
No description

#### Parameters:
- `a`: The multiplicand

- `b`: The multiplier

- `denominator`: The divisor

#### Return Values:
- result The 256-bit result




