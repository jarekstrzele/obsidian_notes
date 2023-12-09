[[8 Higher Order Functions]]

```haskell
-- 1. the same length?
-- 2. the same  element the same order
eql :: [Int] -> [Int] -> Bool
eql xs ys
  | length xs /= length ys = False
  | otherwise = and $ zipWith (==) xs ys

-- zipWith (==) [1,2,3] [1,2,4] -> [True, True, False]
-- and $ zipWith (==) [1,2,3] [1,2,4] -> and [True, True, False] -> True and True and False -> False
-- zipWith (+) [1,2,3] [1,2,4] -> [1+1,2+2, 3+4]
```

----------
```haskell
-- prod [2,10,5] -> 100
-- prod [3,1,2,4] -> 24

prod :: [Int] -> Int
prod [x] = x
prod (x:xs) = x * prod xs

-- FOLDL
-- type: (a->b->a)->a->[b]->a
--      input : foldl (/) 64 [4,2,4]
--      output : 2.0
-- 64 / 4 = 16
-- 16 / 2 = 8
-- 8  / 4 = 2
-- 1* 7 = 7
-- 7 * 2 = 14
-- 14 * 9 = 126
  

prod1 :: [Int]->Int
-- prod1 x = foldl (*) 1 x
prod1 = foldl (*) 1

------------------------------------------------------
-- prodEvens :: [Int]->Int
-- prodEvens x:xs
--     | (x `mod` 2 == 0) = foldl (*) 1 x
--     | otherwise  prodEvens xs

-- filter even [2,1,4,6,7] -> [2,4,6]
-- f . g = f( g(x) )
prodEvens = prod1 . filter even  -- equvalate prodEvens l = prod1 (filter even l)
```


-------------

### `iterate`
```haskell
ghci> iterate (*2) 1       
[1,2,4,8,16,32,64,128,256,512,1024,2048,4 ....

ghci> take 10 $ iterate (*2) 1
[1,2,4,8,16,32,64,128,256,512]
ghci>
```
In Haskell, the `iterate` function is a built-in function that takes:
- a function and
- an initial value as arguments, 
- and returns an infinite list of repeated applications of the function to the initial value.

```haskell
powersOf2 :: [Int]
powersOf2 = iterate (*2) 1

ghci> take 10 powersOf2
[1,2,4,8,16,32,64,128,256,512]
ghci>
```


---------
## scalar product
```haskell
scalarProduct :: [Float]->[Float]->Float -- returns the dot product of two lists of float numbers with the same size
--- scalarProduct [2.0, 1.0, 0.5] [3.0,2.0,2.0] -> 18
scalarProduct [x] [y] = x * y
scalarProduct (x:xs) (y:ys) = x*y + scalarProduct xs ys
  

-- using higer order functions
--- zipWith (+) [1,2,3] [3,2,1]
-- output: [4,4,4]

scalarProduct' x y = sum $ zipWith (*) x y
```

-------------

## flattening lists
```haskell
flatten::[[Int]]->[Int]
-- flatten [[1,2,3],[4,5],[6],[],[3,3]] -> [1,2,3,4,5,6,3,3]
-- flatten xs = concat xs
flatten = concat
-----
-- -- foldr (+) 5 [1,2,3,4]
-- 5 + 4 =9
-- 9 + 3 = 12
-- 12 + 2 = 14
-- 14 + 1 = 15
-- ghci> [1,2,3]++[22,22]
-- [1,2,3,22,22]
flatten' x = foldr (++) [] x -- explicite
-- implicit flatten' = foldr (++) []
```

----
## MyLength
```haskell
myLength :: String -> Int
--myLength "Tomas" -> 5
myLength [x] = 1
myLength (x:xs) = 1 + myLength xs


--- 1. transform the strign into a list of 1's
---     ghci> map (const 1) "TOmas"
--      [1,1,1,1,1]
--- 2. sum all of them
myLength' :: String->Int
-- myLength' s = foldr (+) 0 . (map (const 1) s)
-- myLength' = foldr (+) 0 . map (const 1)
myLength' = foldr ((+) . const 1) 0
```

-----
## Reverse
```haskell
-- myRevers [1.10] -> [10,9,8,7,6,5,4,3,2,1]
myReverse :: [Int] -> [Int]
myReverse [x] = [x]
myReverse (x:xs) = myReverse xs ++ [x]

-- flip (/) 1 2 -> 2 /1 -> 2.0
-- flip (>) 3 5 -> True
-- foldl (/) 64 [4,2,4] -> 2.0
-- 64 / 4 = 16
-- 16 / 2 = 8
-- 8 / 4 = 22.0
reverseHOF :: [Int] -> [Int]
-- reverseHOF x = foldl (filip (:)) [] x
reverseHOF = foldl (flip (:)) []
```


-------
## Occurrences
```haskell
--returns the list that less how many times x appiears in each sublist
-- countIn [[3,2,3],[3], [], [2,2]] 3 -> [2,1,0,0]
countIn :: [[Int]] -> Int -> [Int]
countIn list value = map count list
	where
		count :: [Int] -> Int
		count = length . filter (==value)
-- countIn [[5,2,1], [3], [5], [1,5,5]] 5
-- map count [[5,2,1], [3], [5], [1,5,5]]
----- count [5,2,1] -> length . filter (==5) [5,2,1] -
----- length [5] -> 1
-- ...
```


-----
# FirstWord
```haskell
firstWord :: String -> String -- it returns the first word in the string
-- firstWord " Good moring I sar " -> "Good"
--- dropWhile (<3) [1,2,3,4,5]
--- output: [3,4,5]
--- takeWhile (<3) [1,2,3,4,5]
--- output: [1,2]
firstWord = takeWhile (/=' ') . dropWhile (== ' ')
```


---------
# Conditional Count
```haskell
countIf::(Int->Bool)->[Int]->Int -- returns the number of elmenets in the list that satisfy the predicate
--countIf (>5) [1..10] -> 5
--countIf even [3,4,6,1] ->2
-- filter (>3) [1,2,3,4,5,6,7,8]
--- output: [4,5,6,7,8]
countIf p x = length $ filter p x
```


---
# combination
```haskell
combined :: [Int] -> [Int -> Int] -> [[Int]]
-- returns the list consisting of applying each of the functions
-- in the second list to the elements in the first list
-- combined [1,2,3] [(+1), (*2), (^2)] -> [[2,3,4],[2,4,6], [1,4,9]]
combined list fs = [map f list | f <- fs]
```
----

# consecutive functions
```haskell


```


---
# filter fold
```haskell


```











