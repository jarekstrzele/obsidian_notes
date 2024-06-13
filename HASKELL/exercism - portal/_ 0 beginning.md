

# hello world
```haskell
module HelloWorld (hello) where

hello :: String
hello = "Hello, World!"

main :: IO()
main = putStrLn hello
```

Oto, co się tutaj dzieje:

1. Definiujemy moduł `HelloWorld` i eksportujemy funkcję `hello`.
2. Funkcja `hello` zwraca ciąg znaków `"Hello, World!"`.
3. Definiujemy funkcję `main`, która jest punktem startowym programu Haskell.
4. W funkcji `main` używamy `putStrLn`, aby wypisać wynik funkcji `hello` na ekranie.

	






