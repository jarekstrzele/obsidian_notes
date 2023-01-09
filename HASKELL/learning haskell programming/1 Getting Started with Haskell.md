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






