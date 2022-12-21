
[[1 Basics]]


# SOlved Problems - Functions

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












