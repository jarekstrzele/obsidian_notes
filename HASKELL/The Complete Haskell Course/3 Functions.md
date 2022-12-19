#haskell/function 


# Functions

- functions in Haskell are *pures*: they only return results calculated relative to their parameters
- functions do not have *side effects*:
	- they do not modify the parameters
	- they do not modify the memory 
	- they do not modify the input/output
- a function always returns the same result applied to the same parameters

>	FUNCTION IDENTIFIERS START WITH A lowercase

1. First, its type declaration (header) is given
2. Then its definition is given, using formal parameters

```haskell
double :: Int -> Int
double x = 2 * x

factorial :: Integer -> Integer
factorial n = if n == 0 then 1 else n * factorial (n-1)
```

## Definition with Patterns
Functions can be defined with patterns
```haskell
factorial :: Integer -> Integer

factorial 0 = 1
factorial n = n * factorial (n-1)
```
The evealutation of the patterns is from top to bottom and returns the result of the first matching branch

Patterns are considered more elegant thant `if-then-else` and the have many more applications

`_` **anonymous variable**
```haskell
nand: Bool -> Bool -> Bool       -- negated conjuction

nand True True = False
nand _ _ = True
```

## Definition with Guards

> `| guard = ...`

```haskell
valAbs :: Int -> Int

valAbs n
	| n >= 0 = n
	| otherwise = -n
```
Guard evaluation is top-down and returns the result of the first true branch.

Pattern definitions can also have guards.

## Local Definitions
to define local names in an expression it is used the `let-in`:
```haskell
-- fast exponentiation
fastExp :: Integer -> Integer -> Integer

fastExp _ 0 = 1
fastExp x n = 
	let y = fastExp x n_halved
		n_halved = div n 2
	in
		if even n
		then y * y
		else y * y * x
```

with `where`
```haskell
-- fast exponentiation
fastExp :: Integer -> Integer -> Integer

fastExp _ 0 = 1
fastExp x n = 
	| even n = y * y
	| otherwise = y * y *x
	where
		y = fastExp x n_halved
		n_halved = div n 2
```

The indentation of the `where` defines its scope.

## Currying
All functions have a single parameter.
Functions of more than one parameter actually return a new function.
No need to pass all parameters (partial application)
**Example:**
`prod 3 5` is, i reality, `(prod 3) 5` First we apply `3` and the result is a function that expects another integer.

```haskell
prod :: Int -> Int -> Int
prod :: Int -> (Int->Int)

(prode 3) :: (Int->Int)
(prod 3) 5 :: Int
```


## Solve Problems -- Functions
 remotes/origin/master








