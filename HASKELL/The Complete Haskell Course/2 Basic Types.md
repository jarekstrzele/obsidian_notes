#haskell/types
[[_ 0 Complete Haskell Course]]

---
# Basic Type

Booleans: `Bool`
Integers: `Int`, `Integer`
Reals: `Float`, `Double`
Characters: `Char`

## Bool
type: Boole
literals: False i True
operation: not, ||, &&


## Integer
- type:
	- `Int`: 64 bits integer
	- `Integer`: Integers( arbitratily long)
- literals: `15`, `(-22)`, `34235945830495834
- operations: ``+ - * div mod rem ^`
- relational operators: `> < <= >= == /= (no !=)`


## Reals
- type
	- `Float` 32-bit floating-point reals
	- `Double` 64-bit floating -point reals
- literals: 3.14, 1e-9, -3.0
- operation: `+ - * / **`
- relational operators: `< > => <= == /=`
- integer ro Real conversion: `fromIntegral`
- Real to Integer conversion: `round floor ceiling`

## Characters
type: `Char`
literals: `a A \n`
relational operators: ` < > >= <= == /=`
conversion functions: (it is necessary `import Data.Char`)
`ord::Char->Int`
`chr::Int->Char`

## Predefined Functions
```haskell
even :: Integral a => a->Bool
odd :: Integral a => a->Bool

min :: Ord a => a->a->a
max :: Ord a => a->a->a

-- greatest common divisor
gcd :: Integral a => a->a->a

-- least common multiple
lcm :: Integral a=> a->a->a

-- maths
abs :: Num a => a->a
sqrt :: Floating a=> a->a
log :: Floating a=> a->a
exp :: Floating a=> a->a
cos :: Floating a=> a->a
```


----
Attention:
- the negative sign with parentheses `(-22)`
- `mod` and `rem` work differently with negative numbers
- not identical `/=`


