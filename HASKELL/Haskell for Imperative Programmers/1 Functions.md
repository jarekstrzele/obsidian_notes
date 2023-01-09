[[_ 0 Haskell for Imperative Programmers]]


# Functions 
https://www.youtube.com/watch?v=pitjnqRKyyI&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=2

## Definition

`name arg1 arg2 ... argn = <expression>`
`<expression>` - it is what the function returns

## Application
`name ar1 arg2 ... argn`

## Example
```haskell
in_range min max x = 
	x >= min && x <=max

in_range 0 5 3
True

in_range 4 5 3
False

```

--------------
## Types
Every value in Haskell has a type and that type is strict

```haskell
x :: Integer`
x = 1

y ::  Bool
y = True

z :: Float
z = 3.14154
```

```haskell
in_range :: Integer -> Integer -> Integer -> Bool
in_range min max x = 
	x >= min && x <=max
```

----
## `let` bindings, `where` bindings
to write something like
```
in_range min max x = 
	in_lower_bound = min <=x ;
	in_upper_bund = max >= x;
	return (in_lower_bound && in_upper_bund);
```

use `let ... in`
```haskell
in_range min max x = 
	let 
		in_lower_bound = min <=x
		in_upper_bund = max >= x
	in
	in_lower_bound && in_upper_bound
```

or use `where`
```haskell
in_range min max x =  ilb && iub
	where
		ilb = min <=x
		iub = max >= x
```

---
## Infix
```haskell
add a b = a+b

add 10 20

10 `add` 20
```






