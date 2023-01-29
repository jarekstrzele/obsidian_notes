[[_ 0 Learing Path Haskell]]
[[1.1 Whitespace, Layout and Scoping]]
[[1.2. Values and Expressions]]
[[1.3 Types and Type Signatures]]
[[1.4 Algebraic Data Types]]
[[1.5 Type classes]]
[[1.6 Pattern Matching]]

----
[[2.1 Exploring Haskell]]
[[3 Mastering Haskell Programming]]


# First Haskell Programs

```haskell
-- main is putStrLn hello world
main = putStrLn "Hello world"
--- semantically, this program binds the name `main` to the expression 
```

`putStrLn` the func that takes a single artg of type string and eveluates to an action that when executable string s the terminal and produce no result

in the terminal:
`stack runghc Program.hs`
`runghc` it is an interpreter 

`main::IO()` this means `main` is a function that evaluates to an action which produces no value

```haskell
main :: IO ()

main = do
    content <- readFile "nums.txt"
    putStrLn content
```

`do` is pronounce *from the code* or *drawn form*
*content is drawn from read file applied to nums.txt*

#haskell/print
`print` can be applied to any value that implements the Show type class and is typically used to display a representation of a value for diagnostic purposes 

`putStrLn` is used to output a string folow ya newline character


```haskell
readInts :: String -> [Int]
readInts s = let ws = words s in map read ws

minMax :: Ord a => [a] -> Maybe (a, a)
minMax (h : t) = Just $ foldr
    (\x (min, max) -> (if x < min then x else min, if x > max then x else max))
    (h, h)
    t
minMax _ = Nothing

main :: IO ()
main = do
    content <- readFile "nums.txt"
    let values = readInts content
        count = length values
        total = sum values
        mean = fromIntegral total / fromIntegral count
        range = minMax values
    print count
    print total
    print mean
    print range
```


------------------
```


-----
# GHCI
#ghci

**ghc** stands for "Glasgow Haskell Compiler"
**ghci** is "GLasgow Haskell Compiler Interactive"

`:!` you can use bash command
`:!dir`

### `it`
```ghci
ghci> it

<interactive>:3:1: error:
    * Variable not in scope: it
    * Perhaps you meant `id' (imported from Prelude)
ghci> x = 1
ghci> y = 11
ghci> x+y
12
ghci> it
12
ghci>
```

`:type <value>` 
`:kind <class>`

```ghci
ghci> :t x
x :: Num a => a
ghci> :t Num

<interactive>:1:1: error:
    * Illegal term-level use of the type constructor `Num'
        imported from `Prelude' (and originally defined in `GHC.Num')
    * In the expression: Num
ghci> :kind Num
Num :: * -> Constraint
```

`prettyPrint`
`:run`
`:main`

### debugging with 
`> echo %APPDATA%`

GHCI can privde powerful insights into the *runtime* behaviour of programs

`:break <name>` -> `:break minMax` (where `minMax is a function defined in a file`)
	`:sprint ...`
	`:continue`
	`:list`
	`:show breaks`
	`:show bindings`
	`:abondon`


----

























