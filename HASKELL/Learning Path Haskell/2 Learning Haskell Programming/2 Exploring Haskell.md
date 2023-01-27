[[_ 0 Learing Path Haskell]]

#cassimally_hakim 
- you will use `stack`
- `stack ghci`


# Built-in data type
## lists
`"Hello" <-> ['H', 'l', 'l', 'o']`
`data [] a = [] | a: [a]`
`[1..10]`
`[1,2] ++ [3,4,5]`
*tail*, *head*, 

## tuples
`(1, "sth", True)`
`[(1,"cos"), (False, True)]`

## simple dictionary
`[("one", 1), ("two", 2)]`

```haskell
ghci> :i lookup
lookup :: Eq a => a -> [(a, b)] -> Maybe b
  	-- Defined in ‘GHC.List’

ghci> let dict = [("one", 1), ("two", 2)]
ghci> dict
[("one",1),("two",2)]
ghci> lookup "one" dict
Just 1
ghci> lookup "two" dict
Just 2
ghci> lookup "three" dict
Nothing



```

## Maybe
#haskell/maybe 
```haskell
ghci> :info Maybe
type Maybe :: * -> *
data Maybe a = Nothing | Just a
  	-- Defined in ‘GHC.Maybe’
```

---------
# Editing Haskell Source Code
`main` is a special to Haskell and GHC


```haskell
main :: IO()
main = putStrLn "Hello World!"

----
ghci> :l test.hs 
[1 of 1] Compiling Main             ( test.hs, interpreted )
Ok, one module loaded.
ghci> main
Hello World!
ghci> :main
Hello World!

```


```haskell
main :: IO()
main = putStrLn $ greet  "World!"

greeting = "Hello"
greet who = greeting  ++ ", " ++ who

----
ghci> main
Hello, World!
ghci> greet "Me"
"Hello, Me"
ghci> greeting
"Hello"

```

In GHCI `:set editor vim` -> `:edit`

in the terminal:
`stack ghc fileName.hs`-> after compilation `./fileName`
or
`stack ghc -- -dynamic fileName`

-----------
# Functions
#haskell/function 

```haskell
add a b = a + b
--- Int -> (Int -> Int)
-- 1 -> (2 -> 3)
ghci>:t add 1
add 1 :: Int -> Int
> add1 = add 1
> add1 2
3
-- length "str" -> 3

```

If you have two functions with parameters on the right you can simply get rid of them and instead use what's called a **partially applied function**.
```haskell
add a b = a + b
add 1 2 
3

add1 = add 1
add1 2
3

add1 b = add 1 b
add1 2
3

add a b = (+) a b
add a = (+) a
add = (+) -- add is simplu a synonym or binding for the plus operator




```


----
# Data Structure

## synonym - for more readability
```haskell
type String = [Char]
type Count = Int
processString :: String -> Count

```



# data type
### data types referring to addition
```haskell
data Compass = North | East | South | West

instance Show Compass where
  show North = "North"
  show East = "East"
  show South = "South"
  show West = "West"
                     
```

```haskell
data Compass = North | East | South | West
  deriving (Eq, Ord, Enum, Show)
                     
```


### d

















