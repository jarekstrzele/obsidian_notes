[[_ 0 Complete Haskell Course]]

---
[[1 Basics]]


---

# Solved Problems - Functions

## Absolute Value
Write a function `absValue:: Int->Int`

```haskell
absValue :: Int -> Int
absValue x
        | x >= 0 = x
        | otherwise = -x
```


## Power
`power :: Int->Int->Int`
given an integer x and a natural p, returns thep-th power of x, that is x^p

```haskell
power :: Int -> Int -> Int

power x 0 = 1 -- base case
power x p
  | even p = n * n
  | otherwise = n*n*x
  where
    n = power x (p `div` 2)
```


## Prime Number
>[!info] Prime Number
>It is a whole number greater than 1 whose only factors are 1 and itsself.


```haskell
isPrime :: Int -> Bool

isPrime 0 = False
isPrime 1 = False

isPrime x = not (hasDivisor (x-1))
	where
		hasDivisor :: Int -> Bool
		hasDivisor 1 = False
		hasDivisor n = mod x n == 0 || hasDivisor(n-1)
```

## Fibonacci Sequence
>[!info] Fibonacci Sequence
>each number is a sum of tow preceding ones

$fib(0)=0$
$fib(1)=1$
$fib(n)=fib(n-1)+fib(n-2)$ for $n>=2$









