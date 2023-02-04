
# Infinite ones
```haskell
ones :: [Integer]
-- take 3 ones --> [1,1,1]
-- repeat :: a -> [a]
-- repeat 9 -> [9,9,9....]
ones = repeat 1
```


---
 # integers
 ```haskell
 ints :: [Integer]
-- take 8 ints ---> [0,1,-1,2,-2,3,-3,4]
ints = iterate integers 0
  where
    integers :: Integer -> Integer
    integers x
      | x > 0 = -x
      | otherwise = 1 - x
```

------
# Natura Numbers

```haskell
nats :: [Integer]
-- it returns a infinite list of natural numbers
-- iterate (*2) 1 --> [1,2,4,8,16,....]
-- ghci> :t iterate
-- iterate :: (a -> a) -> a -> [a]
nats = iterate (+1) 0
```


-----
# triangular numbers
```haskell
triangulars::[Integer]
-- take 8 triangulars [0,1,3,6,10,15,21,28]
-- * T1=1
-- T3 = 6
-- *
-- **
-- ***
-- Tn = sum_k=1_n k = 1+2+3+4+...+ n = n(n+1)/2
-- T3 = 3(3+1)/2 = 3*4/2 = 12/2 =6
-- iterate (*2) 1 -> [1,2,4,8,16,...]

-- scanl operation initial_element list
-- scanl (/) 64 [4,2,4]
-- [64.0, 16.0, 8.0, 2.0]
-- 64/4 = 16
-- 16/2 = 8
-- 8/ 4 = 2
triangulars = scanl (+) 0 $ iterate (+1) 1
```

--------
# Factorial Dimension
```haskell

```























