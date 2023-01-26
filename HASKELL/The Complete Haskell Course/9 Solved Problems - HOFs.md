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
```











