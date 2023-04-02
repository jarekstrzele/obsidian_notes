**[[_ 0 Learining Haskell Programming]]

[[#Built-in Data Structures]]
[[#Editing Haskell Source Code]]
[[#Intro to Function]]
[[#Build Your Own Data Structures]]
[[#Pattern Matching]]

----

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


----
# Editing Haskell Source Code

`vim test.hs`
```haskell
main = putStrLn "Hello from Haskkel!!!"
```
load it to ghci `:l test.hs`
run the function `main`

```haskell
main = putStrLn (greet "World")

greeting = "Hello"
greet who = greeting ++ ", " ++ who 
```
ghci> :r
[1 of 1] Compiling Main             ( first_haskell.hs, interpreted )
Ok, one module loaded.
ghci> main
Hello, World

## to trigger the editor from `ghci`
`:set editor vim`
`:edit `

## to compile
`>stack ghc file.hs`
`>./file`

```bash
e> stack ghc .\first_haskell.hs
[1 of 1] Compiling Main             ( first_haskell.hs, first_haskell.o )
Linking first_haskell.exe ...
PS C:\Users\jaros\Desktop\Prog\haskell_simple_console> .\first_haskell.exe
New ONE, World
```

## to do some optymalization:
### `stack ghc -- -dynamic file.hs`


----
# Intro to Function

![[HaskelFunc.excalidraw | 500 ]]
>[!info] Haskell functions
>THey are very much lik mathematical functions in that they map from values of a certain type like strings to values of another type like integers

```haskell
ghci> add a b = a + b
ghci> add 1 3
4


```

```haskell
add :: Int -> Int -> Int
add a b = a + b

ghci> add1 b = add 1 b
ghci> add1 10
11

ghci> :t add
add :: Num a => a -> a -> a
ghci> :t add 1
add 1 :: Num a => a -> a
```

----
# Build Your Own Data Structures

## Type synonyms
```haskell
type Count = Int

processString :: [Char] -> Count
processString = undefined

---------------------------------------
ghci> :l func_haskell.hs
[1 of 1] Compiling Main ( func_haskell.hs, interpreted )
Ok, one module loaded.
ghci> :t processString
processString :: [Char] -> Count
ghci>
```



## Composite data types (ADT - *Abstract Data Type*)

### Pattern
```haskell
ghci> :info Bool
type Bool :: *
data Bool = False | True
```

```haskell
data Compass = North | East | Sount | West

----------
ghci> :i Compass
type Compass :: *
data Compass = North | East | Sount | West
        -- Defined at data_haskell.hs:1:1
```

to show Compass
```haskell

data Compass = North | East | Sount | West

instance Show Compass where
  show North = "North"
  show East = "East"
  show South = "South"
  show West = "West"

ghci> :r
Ok, one module loaded.
ghci> North
North
ghci> ABs

<interactive>:22:1: error: Data constructor not in scope: ABs
```

to compare Compass
```haskell
instance Eq Compass where 
	North == North = True
--- .....
```

you can use `deriving` :

#### addition
```haskell
--- that referrring to addition
data Compass = North | East | South | West
   deriving (Eq, Ord, Enum, Show)

---------------
[1 of 1] Compiling Main  ( data_haskell.hs, interpreted )
Ok, one module loaded.
ghci> East > North
True
ghci> North
North
ghci> South == West
False
ghci> succ West
East 
```


#### multiplication
`data Maybe a = Nothing | Just a`
**the constructor takes additional parameters**
```haskell
data Expression = Number Int
				| Add Expression Expression
				| Substract Expression Expression
				deriving (Eq, Ord, Show)
```

----
# Pattern Matching

```haskell
data Expression = Number Int
   | Add Expression Expression
   | Substract Expression Expression
   deriving (Eq, Ord, Show)
   
calc :: Expression -> Int
calc (Number x) = x

---------
ghci> calc (Number 1)
1
ghci> calc (Number 119)
119
ghci> calc (Add (Number 1) (Number 10))
*** Exception: data_haskell.hs:11:1-19: Non-exhaustive patterns in function calc



```

```haskell
data Compass = North | East | South | West
   deriving (Eq, Ord, Enum, Show)
   
   
data Expression = Number Int
   | Add Expression Expression
   | Subtract Expression Expression
   deriving (Eq, Ord, Show)
   
calc :: Expression -> Int
calc (Number x) = x
calc (Add x y) = (calc x) + (calc y)
calc (Subtract x y) = (calc x) - (calc y)


-----
ghci> calc (Number 12)
12
ghci> calc (Add (Number 34) (Number 56))
90
ghci> calc (Add (Number 34) (Subtract (Number 56) (Number 21)))
69
```

### list
```haskell
newHead :: [a] -> a
newHead [] = error "empty list"
newHead (x:xs) = x

newTail :: [a] -> [a]
newTail [] = error "empty list"
newTail (X:Xs) = xs

```


