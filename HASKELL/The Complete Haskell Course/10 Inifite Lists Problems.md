
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
factorials :: [Integer]
-- 0!-1, 1!-1, 2!-2,3!-6,4!-24, 5!-120
-- take 4 factorials -> [1,1,2,6]
-- scanl, iteratate
factorials = scanl (*) 1 $ iterate (+1) 1
```


---
# Prime Numbers
```haskell
primes :: [Integer]
--- take 6 primes [2,3,5,7,11,13]
-- [1,2,3,4,5,6,7,8,9,...]
-- filte the prime ones
--- iterate f x ----> [x, f(x), f(f(x)), (f(f(f(x)))]
primes = filter isPrime $ iterate (+1) 1
 where
  isPrime :: Integer -> Bool
  isPrime 1 = False
  isPrime 2 = True
  isPrime n
    | even n = False
    | otherwise = isPrimeAux 3
       where
         isPrimeAux :: Integer -> Bool
         isPrimeAux x
            | x >= div n 2 = True
            | mod n x == 0 = False
            | otherwise = isPrimeAux (x+2)
-- for each odd number
-- we chack if n is divisible by [2,5,7,9, 11 ,...]
```

----
# Hamming numbers
























