
`ghc` an optimizing compiler that generates fast native code
`ghci` an interactive interpreter and debugger
`runghc` a program for running Haskell program as scripts, without needing to compiule them first

```haskell
ghci> 2+2
4
ghci> (+) 2 2
4
ghci> 2 + (-3)
-1
ghci> True || False
True
ghci> True && False
False
ghci> 1 == 1
True
ghci> 1 < 3
True
ghci> 2 == 3
False
ghci> 2 /= 3
True
ghci>
```

in `ghci` to define `let e = exp 1`
```haskell
ghci> let e = exp 1
ghci> e
2.718281828459045
ghci>
```

# List
```haskell
ghci> [1..10]
[1,2,3,4,5,6,7,8,9,10]
ghci> [1.0, 1.25..2.0]
[1.0,1.25,1.5,1.75,2.0]
ghci>
ghci> putStrLn "Here's a newline -->\n<-- see?"
Here's a newline -->
<-- see?
```

# Types
```haskell
ghci> :set +t
ghci> 'c'
'c'
it :: Char
ghci> "foo"
"foo"
it :: String
ghci> it ++ "bar"
"foobar"
it :: [Char]
ghci> it ++3

<interactive>:24:6: error:
    * No instance for (Num [Char]) arising from the literal `3'
    * In the second argument of `(++)', namely `3'
      In the expression: it ++ 3
      In an equation for `it': it = it ++ 3
ghci> :t 'a'
'a' :: Char
ghci> :t "a"
"a" :: String
ghci> 3+2
5
it :: Num a => a
ghci> :t it
it :: Num a => a
ghci> pred 9
8
it :: (Enum a, Num a) => a
ghci> :t it
it :: (Enum a, Num a) => a
ghci> sin (pi/2)
1.0
it :: Floating a => a
ghci> :?
```






