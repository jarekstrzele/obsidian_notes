*hello.hs*
```haskell
module Main where

main :: IO ()
main = do
    putStrLn "Hello, WOrld!"
```
- `module Main where` definiuje moduł o nazwie `Main`. Moduł to jednostka kompilacji w Haskellu.
- `main :: IO ()` definiuje funkcję `main`. Funkcja `main` jest funkcją punktu wejścia do programu.
- `main = do` definiuje blok kodu, który jest wykonywany przez funkcję `main`.
- `putStrLn "Hello, World!"` wyświetla napis "Hello, World!" na konsoli.

```powershell
> ghc .\hello.hs
> .\hello.exe
> Hello, WOrld!
```

# Funkcja

```haskell
module Main where
  

add :: Int->Int->Int
add x y = x + y
  

main :: IO ()
main = do
    putStrLn "Hello, WOrld!"
    print (add 10 10)  -- Użyj funkcji `print` do wyświetlenia wyniku
```

`main::IO()` specjalna funkcja  w Haskellu, od której rozpoczyna się wykonywanie programu. Jest ona typu `IO()`, co oznacza, że wykonuje operacje wejścia/wyjścia
`do` blok kodu wewnątrz funkcji `main` 

```haskell
module Main where

factorial :: Int->Int
factorial 0 = 1
factorial n = n * factorial(n-1)

factorial' :: Int->Int
factorial' n = if n == 0 then 1 else n * (n-1)

main :: IO ()
main = do
    putStrLn "Hello, WOrld!"
    print (factorial' 10)
    putStrLn ("10! = " ++ show(factorial 10))
```






