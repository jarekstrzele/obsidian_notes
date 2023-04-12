# A Basic structure of a Haskell File

```haskell
-- Deklaracja modułu
module Main where

-- Importowanie modułów
import Data.List

-- Definicje funkcji
sumSquares :: Int -> Int -> Int
sumSquares x y = x^2 + y^2

factorial :: Integer -> Integer
factorial n = product [1..n]

main :: IO ()
main = do
  putStrLn "Hello, World!"
  putStrLn $ "Sum of squares of 3 and 4: " ++ show (sumSquares 3 4)
  putStrLn $ "Factorial of 5: " ++ show (factorial 5)

```

```haskell
-- Deklaracja modułu
module Main where

-- Importowanie modułów
import Data.List (sort)

-- Deklaracja funkcji
doubleList :: [Int] -> [Int]
doubleList xs = map (*2) xs

-- Funkcja main
main :: IO ()
main = do
  let list = [3, 7, 2, 9, 1]
  putStrLn $ "Original list: " ++ show list
  let sortedList = sort list
  putStrLn $ "Sorted list: " ++ show sortedList
  let doubledList = doubleList list
  putStrLn $ "Doubled list: " ++ show doubledList

```