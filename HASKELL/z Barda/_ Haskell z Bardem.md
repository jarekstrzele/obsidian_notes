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

### `data Punkt = Punkt Int Int` lub
```haskell
data Punkt = Punkt Int Int deriving (Show, Eq)
p1::Punkt
p1 = Punkt 11 23

main :: IO()
main = do
    putStrLn "Typy danych"
    print p1
```
wyświetlenie pojedynczych współrzędnych
```haskell
main :: IO()
main = do
    putStrLn "Typy danych"
    case p1 of
        Punkt x y -> do
            putStrLn ("Współrzędna x: " ++ show x)
            putStrLn ("Współrzędna y: " ++ show y)
```

1. `case p1 of`: Rozpoczynamy instrukcję `case`, która służy do dopasowania wzorca do wartości `p1`.
2. `Punkt x y -> do`: W tej części definiujemy wzorzec dopasowania. Wzorzec ten mówi, że jeśli `p1` ma konstruktor `Punkt` z dwiema argumentami, to przypisz te argumenty do zmiennych `x` i `y`.
	`->` oznacza, że po prawej stronie ma nastąpić odpowiednia akcja, jeśli wzorzec pasuje.
    

### `data Punkt = Punkt {x:: Int, y:: Int}`
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


## użycie typu danych w funkcji

>   In Haskell, `fromIntegral` is a commonly used function that is used to **convert** a value of one numeric type into another. It is particularly useful when you need to convert between different numeric types, such as from an integral type (like `Int` or `Integer`) to a floating-point type (like `Float` or `Double`), or vice versa.

```haskell
module Main where

data Punkt = Punkt Int Int deriving (Show, Eq)

odlegloscOdPoczatku :: Punkt -> Double
odlegloscOdPoczatku (Punkt x y) = sqrt $ fromIntegral (x^2 + y^2)

main :: IO()
main = do
    putStrLn "Typy danych"
    let p1 = Punkt 11 23
    let distance = odlegloscOdPoczatku p1
    putStrLn $ "Odległość od początku układu współrzędnych: " ++ show distance
```

przykład z typem danych Kwadrat
 > składnia GADT (Generalized Algebraic Data Types), która pozwala na bardziej precyzyjne opisanie typów danych.

```haskell
module Main where

-- Zdefiniuj typ danych Kwadrat, który ma jeden
-- konstruktor Kwadrat przyjmujący jeden argument typu Int.
-- Zdefiniuj funkcję pole przyjmującą jako argument kwadrat
--  i zwracającą jego pole powierzchni.

data Kwadrat where
  Kwadrat :: {a :: Int} -> Kwadrat deriving(Show, Eq)


obliczPole :: Kwadrat -> Double
obliczPole (Kwadrat a) = fromIntegral (a*a)

main::IO()
main = do
    print "Haskell z Bradem i ChatGPT"
    let kw = Kwadrat 10
    let pole = obliczPole kw
    print (show kw ++ ", pole: " ++ show pole) 
```
> - The code you've provided is a definition of a data type in Haskell called `Kwadrat` using ==record syntax==.
> 1. `data Kwadrat`: This line declares a new data type called `Kwadrat`. 
> 2. `Kwadrat :: { a :: Int }`: This part defines a data constructor for the `Kwadrat` type. A data constructor is a way to create values of the data type. In this case, the data constructor is also defined using record syntax, which means that it includes a named field. The field is named `a`, and its type is `Int`. This means that when you create a `Kwadrat` value, you need to provide an integer value for the `a` field. For example, `Kwadrat { a = 5 }`.
> 3. `deriving (Show, Eq)`: This part tells Haskell to automatically generate instances of the `Show` and `Eq` type classes for the `Kwadrat` data type. This allows you to print `Kwadrat` values using `show` and compare them for equality using ` == `.
















