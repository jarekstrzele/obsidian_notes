
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







