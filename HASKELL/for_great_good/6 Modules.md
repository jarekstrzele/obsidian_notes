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
### `ghci> :m +Data.List`
### `ghci> :m + Data.List Data.Map Data.Set`

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

> `intercalate` 
> - **takes**:
> 	- a list of lists and
> 	- a list. 
> - **inserts** that list in between all those lists and then dlattens the result
```haskell
ghci> intercalate " " ["hey", "there", "gays"]
"hey there gays"
ghci> intercalate [1,2,3] [[22,33], [11, 22], [77,88], [91,92]]
[22,33,1,2,3,11,22,1,2,3,77,88,1,2,3,91,92]

ghci> intercalate [1,2,3] [[22,33], [11, 22], [77,88], [91,92, 100]]
[22,33,1,2,3,11,22,1,2,3,77,88,1,2,3,91,92,100]

ghci> intercalate [1,2,3] [[22,33], [11, 22.212], [77,88], [91,92, 100]]
[22.0,33.0,1.0,2.0,3.0,11.0,22.212,1.0,2.0,3.0,77.0,88.0,1.0,2.0,3.0,91.0,92.0,100.0]
```

> `transpose` transposes a list of lists
> columns become rows

```haskell
import Data.List
let a = transpose [[1,2,3], [4,5,6], [7,8,9]]

output: [[1,4,7],[2,5,8],[3,6,9]]
```

Say we have the polynomials 
- $3x2 + 5x + 9$,
- $10x3 + 9$ 
- $8x3 + 5x2 + x - 1$
and we want to add them together. We can use the lists [0,3,5,9], [10,0,0,9] and [8,5,1,-1] to represent them in Haskell. 
Now, to add them, all we have to do is this:
```haskell
ghci> map sum $ transpose [[0,3,5,9],[10,0,0,9],[8,5,1,-1]]  

output: [18,8,6,17]
```


`concat` flattens a list  of lists  into just  just a list of elements
```haskell
1.  ghci> concat ["foo","bar","car"]  
2.  "foobarcar"  
3.  ghci> concat [[3,4,5],[2,3,4],[2,1,1]]  
4.  [3,4,5,2,3,4,2,1,1]
```

`concatMap` maps and concats list
```haskell
1.  ghci> concatMap (replicate 4) [1..3]  
2.  [1,1,1,1,2,2,2,2,3,3,3,3]

-- Funkcja main
main :: IO ()
main = do
  let a = concatMap (replicate 4) [1..3]
  print a
  let b = replicate 4 5
  print b

[1,1,1,1,2,2,2,2,3,3,3,3]
[5,5,5,5]
```

`and` takes a list  of boolean and returns `True` only if all  the values in the list are  True



......

-------------
# Data.Char
It exports functions that deal with characters. Its also helpful when filetering and mapping over strings because they are just lists of characters



...


---------
# Data.Map
Association lists (also called dictionaries) are lists that are used to store key-value pairs where ordering doesn't matter


An association list with phone numbers (*list of pairs*, first component a **key**, the second one a **value**)
```haskell
-- Deklaracja modułu
module Main where

-- Importowanie modułów
import Data.List

-- Deklaracja funkcji
phoneBook =   
    [("betty","555-2938")  
    ,("bonnie","452-2928")  
    ,("patsy","493-2928")  
    ,("lucille","205-2928")  
    ,("wendy","939-8282")  
    ,("penny","853-2492")  
    ]  

findKey :: (Eq k) => k -> [(k,v)] -> v
findKey key xs = snd . head . filter (\(k,v) -> key == k) $ xs

fK :: (Eq k) => k -> [(k,v)] -> Maybe v
fK key = foldr (\(k,v) acc -> if key == k then Just v else acc) Nothing

-- Funkcja main
main :: IO ()
main = do
  print phoneBook 
  print $ findKey "penny" phoneBook
  print $ fK "penny" phoneBook

output
[("betty","555-2938"),("bonnie","452-2928"),("patsy","493-2928"),("lucille","205-2928"),("wendy","939-8282"),("penny","853-2492")]
"853-2492"
Just "853-2492"
```

> The `Data.Map` module offers **association lists that are much faster** (because they're internally implemented with trees) and also it **provides a lot of utility functions**.

>[!info] Mapa
> W Haskellu mapa jest reprezentowana przez moduł `Data.Map`, który udostępnia wiele funkcji do manipulowania mapami. Na przykład, możemy
> 	- *dodać* parę klucz-wartość do mapy za pomocą funkcji `insert`, 
> 	-  *usunąć *element za pomocą funkcji `delete`,
> 	- *wyszukać* wartość odpowiadającą danemu kluczowi za pomocą funkcji `lookup`. 
> Mapy w Haskellu są implementowane jako drzewa poszukiwań binarnych, co oznacza, że operacje na mapach mają złożoność czasową O(log n), gdzie n to liczba elementów w mapie.
#haskell/map


## `import qualified Data.Map as Map`
> Kod importu `import qualified Data.Map as Map` oznacza, że ​​moduł `Data.Map` został zaimportowany do bieżącego modułu Haskell, ale z zastosowaniem jakościowego identyfikatora `Map`.
>
> `qualified` wskazuje, że ​​przywołanie funkcji lub typów z modułu `Data.Map` będzie wymagało użycia jakościowego identyfikatora `Map`. Dzięki temu można uniknąć kolizji nazw z innymi funkcjami lub typami w module, w którym jest wykorzystywany moduł `Data.Map`.
>
>Na przykład, jeśli `Data.Map` zawiera funkcję o nazwie `size`, to można jej użyć w bieżącym module za pomocą `Map.size`.


#### `fromList` function
takes an association list (in the form of a list) and returns a map with the same associations

```haskell

import qualified Data.Map as Map

-- Tworzymy mapę par nazwisk i wieku
ages = Map.fromList [("Alice", 25), ("Bob", 30), ("Charlie", 35)]

-- Dodajemy parę do mapy
ages' = Map.insert "David" 40 ages

-- Usuwamy element z mapy
ages'' = Map.delete "Charlie" ages'

-- Wyszukujemy wartość dla klucza
age = Map.lookup "Bob" ages''

```

.....

---
# Data.Set
Sets are kind of like across between lists and maps




