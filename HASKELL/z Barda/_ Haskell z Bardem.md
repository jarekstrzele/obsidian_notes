#haskell 

----------
```bash
> ghc nazwaPliku.hs
> ./nazwaPliku
```

----
Zawartość Notatki:
[[#HelloWorld]]
[[#Funkcja]]
[[#Typy danych]]


----
# HelloWorld
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

------------
# Typy danych
- proste - reprezentują pojedynczą wartość Int, Char, Bool, ..
- złożone - reprezentują zbiory wartości:  List, Tuple, Maybe, Either 

## Definiowanie typów danych
Typy danych można definiować za pomocą słowa kluczowego `data`.

`data NazwaTypuDanych = Konstr1 Typ1 | Konstr2 Typ2`

`data Punkt = Punkt Int Int` lub
`data Punkt = Punkt {x:: Int, y:: Int}`
```haskell
data Punkt = Punkt {x:: Int, y:: Int}

let punkt = Punkt {x = 3, y = 4}
let xWspolrzedna = x punkt

```

> ==w Haskellu, aby uzyskać dostęp do pól rekordu, używasz ich nazw zamiast operatora kropki.==

```haskell
module Main where

data Punkt = Punkt {x :: Int, y :: Int} deriving (Show, Eq)
p1::Punkt
p1 = Punkt {x=2, y=3}

main :: IO()
main = do
    putStrLn "Typy danych"
    print(x p1)
    print(y p1)
```









