https://exercism.org

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


-----
# leap year
A leap year (in the Gregorian calendar) occurs:

- In every year that is evenly divisible by 4.
- Unless the year is evenly divisible by 100, in which case it's only a leap year if the year is also evenly divisible by 400.

Some examples:

- 1997 was not a leap year as it's not divisible by 4.
- 1900 was not a leap year as it's not divisible by 400.
- 2000 was a leap year!

```haskell
module LeapYear (isLeapYear) where

isLeapYear :: Integer -> Bool
isLeapYear year 
  | year `mod` 400 == 0 = True
  | year `mod` 100 == 0 = False
  | year `mod` 4 == 0 = True
  | otherwise = False
  

main :: IO()
main = do
  print (isLeapYear 1900)
```




