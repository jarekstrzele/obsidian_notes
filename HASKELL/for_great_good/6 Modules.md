[[0 - Haskell intro]]

> [!info] Haskell Module
>a collection of related :
>	- functions
>	- types
>	- typeclasses

>[!info] Haskell program
>a collection of modules where the main module:
>	- loads up the other modules
>	- uses the functions defined in them to do something


# The Haskell standard library
- it  is split into modules
- each of these modules contains functions and types
- modules:
	- for lists
	- for concurrent programming
	- for complex number ...

## `import <module name>`

```haskell
import Data.List

numUniques :: (Eq a) => [a] -> Int
numUniques = length . nub
-- nub is defined in Data.List module
-- nub takes a list and weeds out duplicate elements (weed out - usuwać)
-- composing length and nub produces a function that's the equivalent of
    -- \xs -> length (nub xs)
ghci> :m + Data.List
ghci> nub [1,1,2,2,3,4]
[1,2,3,4]
ghci> numUniques [1,2,3,3,3,2,1,1]
3
ghci>
```


## import module in GHCI
`ghci> :m +Data.List`

`ghci> :m + Data.List Data.Map Data.Set`

`import Data.List (nub, sort)`

all except the `nub` function:
`import Data.List hiding (nub)`

when in a module is a function with the same name as in `Prelude` functions (e.g. `filter` is in `Prelude` and in `Data.Map`) so import like this:
##### `import qualified Data.Map as M`
so now you cant use filter from `Data.Map` by `M.filter`

https://downloads.haskell.org/ghc/latest/docs/libraries/

# `Data.List`
This module is all about lists (e.g. `map`, `filter` Predule module exports these function)

`intersperse` takes an element and a list and then puts that element in between each pair of elements in the list
```haskell
ghci> intersperse '.' "MONKEY"
"M.O.N.K.E.Y"
ghci> intersperse 0 [1,2,3,4,5]
[1,0,2,0,3,0,4,0,5]
ghci> intersperse '&' "DoG"
"D&o&G"
ghci> intersperse 2 [0.3,0.2,0.9]
[0.3,2.0,0.2,2.0,0.9]

```

`intercalate` takes a list of lists and a list. It inserts that list in between all those lists and then dlattens the result





