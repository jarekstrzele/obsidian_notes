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
> functions can take functions as parameters and also return functions

```haskell
applyTwice :: (a->a) -> a -> a
applyTwice f x = f (f x)
```
the first parameter is a function `(a->a)`
```bash
ghci> applyTwice (+3) 10
16
ghci> applyTwice (++ " HhahHAH" ) "Hejka"
"Hejka HhahHAH HhahHAH"
ghci> applyTwice (" HhahHAH" ++ ) "Hejka"
" HhahHAH HhahHAHHejka"
```


```haskell
zipWith' :: (a->b->c) -> [a] -> [b] -> [c]
zipWith' _ [] _ = []
zipWith' _ _ [] = []
zipWith' f (x:xs) (y:ys) = f x y :zipWith' f xs ys
```
```bash

zipWith' :: (a -> b -> c) -> [a] -> [b] -> [c]
ghci> zipWith' (+) [4,2,4,6] [2,6,2,3]
[6,8,6,9]
ghci> zipWith' (zipWith' (*)) [[1,2,3],[3,5,6],[2,3,4]] [[3,2,2],[3,4,5],[5,4,3]]  
[[3,4,6],[9,20,30],[10,12,12]]
```

>[!importent] like interface
>Functional programming uses **higher order functions to abstract away common patterns**, like examining two lists in pairs and doing something with those pairs or getting a set of solutions and eliminating the ones you don't need.


```haskell
flip' :: (a->b->c)->(b->a->c)
flip' f = g
  where g x y = f y x
```
It takes a function that takes `a` and `b` and returns a function that takes a `b` and `a`
`(a -> b -> c) -> (b -> a -> c)` 
is the same as `(a -> b -> c) -> (b -> (a -> c))`
and it is the same as
`(a -> b -> c) -> b -> a -> c`
simpler way
```haskell
flip' :: (a -> b -> c) -> b -> a -> c  
flip' f y x = f x y
```

# map
`map` takes a function and a list and applies that function to every element in the list, producing a new list
```haskell
map :: (a->b) -> [a] -> [b]
map _ [] = []
map f (x:xs) = f x : map f xs
```

`map (+3) [1,5,3,1,6]` is the same as writing `[x`












