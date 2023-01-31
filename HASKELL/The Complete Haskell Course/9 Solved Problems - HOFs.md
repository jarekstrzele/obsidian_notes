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














