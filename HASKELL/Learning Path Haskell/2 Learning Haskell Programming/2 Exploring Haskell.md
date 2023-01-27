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











