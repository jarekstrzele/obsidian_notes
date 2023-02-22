[[0 - Haskell intro]]

>[!info] HOF
> A function that take functions as parameters or return functions as return values.


# Curried functions
==Every functions in Haskell officially only takes one parameter!!==

If a function accepts several parameters is **curried function**

>[!info] parially applied function
>a function that takes as many parameters as we left out


```haskell
ghci> max 4 5
5
ghci> (max 4) 5
5
```

Putting a space between two things is simply **function application!!!**.
The space is sort of like an operator and it has the highest precedence.
`max::(Ord a)=> a->a->a` that can also be written:
`max:(ord a)=>a->(a->a)` - `max` takes an `a` and returns a function that takes an `a` and returns an `a`

----
```haskell
multThree :: (Num a) => a -> a -> a -> a  
multThree x y z = x * y * z
```
so
`multThree 3 5 9` --> `((multThree 3) 5) 9`
1. `3` is applied to the function (they are separated by space)
2. the result will be a function that takes one parameter and returns a function
3. that last function takes `9`  and returns 135
```
multThree 3
3 * 5  = 15
15 * 9 = 135
```

```haskell
compareWithHundred :: (Num a, Ord a) => a -> Ordering  
compareWithHundred x = compare 100 x
```
It returns a function that takes a number and compares it with 100.
so ->
```haskell
compareWithHundred :: (Num a, Ord a) => a ->Ordering
compareWithHundred = compare 100
```

`compare 100` returns a function that takes a number and compares it with 100
```haskell
Prelude> :t compare  
compare :: Ord a => a -> a -> Ordering
```


### infix functions
Infix functions can also be partially applied by using sections
```haskell
divideByTen :: (Floating a) => a -> a
devideByten = (/10)
```
so
calling `divideByTen 200` is equivalent to doing `200/10`, as is doing `(/10) 200`

------
# ## Some higher-orderism is in order










