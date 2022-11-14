[[_ 0 Complete Haskell Course]]


# Basics
- parentheses not necessary
	- `div 14 4` => `3`
- type
	- `:type 'D'` => `'D' :: Char`
	- `:type not ` => `not :: Bool -> Bool`
`:type length` => `length :: [a] -> Int `

```haskell
factorial :: Integer -> Integer

factorial 0 = 1
factoria n = n * factorial (n-1)


```

```haskell
factoria 5
120

map factorial [0..5]
[1,1,2,6,24, 120]
```

## Necessary Tools
- Glasgow Haskel Compiler (GHC)
	- compiler (ghc)
	- interpreter (ghci)
- code editor
- termianl

`sudo apt install ghc`

## Haskell Interpreter
in termianl `ghci`
```bash
$ ghci
GHCi, version 8.8.4: https://www.haskell.org/ghc/  :? for help
Prelude> not (even 25)
True
Prelude> even 25
False
Prelude> 
Prelude> :type even
even :: Integral a => a -> Bool

```

### `fileName.hs`
`program.hs`:
```haskell
factorial :: Integer -> Integer

factoria 0 = 1 -- base case
factoria n = n * factorial(n-1)

double x = 2 * x
```

in `ghci`:
`> :load program.hs`

`>:reload`

>negative numbuers in parenthesis 
>`double (-20)`

