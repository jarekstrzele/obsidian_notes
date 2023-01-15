**[[_ 0 Learining Haskell Programming]]


```haskell
> ghci
GHCi, version 9.2.5: https://www.haskell.org/ghc/  :? for help
ghci> 123+10
133
ghci> "hello" ++ "world"
"helloworld"
ghci> 1.4 /2
0.7
ghci> 1 /2  
0.5
```

## `:type`
```haskell
ghci> :type True
True :: Bool
ghci> :type pi
pi :: Floating a => a
ghci> :type 123
123 :: Num a => a
```

## `:info`
```haskell
ghci> :info Bool
type Bool :: *
data Bool = False | True
        -- Defined in `GHC.Types'
instance Eq Bool -- Defined in `GHC.Classes'
instance Ord Bool -- Defined in `GHC.Classes'
instance Enum Bool -- Defined in `GHC.Enum'
instance Show Bool -- Defined in `GHC.Show'
instance Read Bool -- Defined in `GHC.Read'
instance Bounded Bool -- Defined in `GHC.Enum'
ghci>
```

---
# Built-in Data Structures

```haskell
--list
ghci> [1..10]
[1,2,3,4,5,6,7,8,9,10]

ghci> :i []
type [] :: * -> *
data [] a = [] | a : [a]

ghci> [1,2] ++ [3,4]
[1,2,3,4]



```


```haskell
-- tuple
ghci> :t (1,2,3,4)
(1,2,3,4) :: (Num a, Num b, Num c, Num d) => (a, b, c, d)
ghci> :t (1,2,'3',4)
(1,2,'3',4) :: (Num a, Num b, Num d) => (a, b, Char, d)
ghci> :t (1,2,'3',4, "coś")
(1,2,'3',4, "coś")
  :: (Num a, Num b, Num d) => (a, b, Char, d, String)

[("one",1),("two",2),("three",3)]
ghci> :i lookup
lookup :: Eq a => a -> [(a, b)] -> Maybe b
        -- Defined in `GHC.List'
ghci> let dict = [("one",1), ("two", 2), ("three",3)]
ghci> lookup "one" dict
Just 1
ghci> lookup "four" dict
Nothing
```

#haskell/maybe
**Maybe** is a data type that might return a value or might not


# Editing Haskell Source Code


