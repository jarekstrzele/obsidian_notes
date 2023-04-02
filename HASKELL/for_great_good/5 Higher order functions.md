[[0 - Haskell intro]]

[[#Curried functions]]
[[#Some higher-orderism is in order]]
[[#map]]
[[#filter]]
[[#]]


>[!info] HOF
> A function that take functions as parameters or return functions as return values.


# Curried functions
==Every functions in Haskell officially only takes one parameter!!==

If a function accepts several parameters is **curried function**

>[!info] parially applied function
>
if we call a function with ==too few== parameters, we get back ==a partially applied function==, meaning a function that takes as many parameters as we left out.

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
### Some higher-orderism is in order
>
> functions can take functions as parameters and also return functions
> 

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
#haskell/map
`map` takes a function and a list and applies that function to every element in the list, producing a new list
```haskell
map :: (a->b) -> [a] -> [b]
map _ [] = []
map f (x:xs) = f x : map f xs
```

`map (+3) [1,5,3,1,6]` is the same as writing `[x+3 | x<-[1,5,3,1,6]`

# filter
#haskell/filter
it takes:
- a [[predicate]]
- a list 
returns the list of elems that satisfy the predicate

```haskell
filter :: (a->Bool) -> [a] ->[a]
filter _ [] = []
filter p (x:xs)
  | p x = x : filter p xs
  | otherwise = filter p xs
```

#haskell/quicksort
```haskell
quicksort :: (Ord a) => [a] -> [a]
quicksort [] = []
quicksort (x:xs) =
  let smallerSorted = quicksort (filter (<=x) xs)
      biggerSorted = quicksort (filter (>x) xs)
  in smallerSorted ++ [x] ++ biggerSorted
```


 _find the largest number under 100,000 that's divisible by 3829_. 
 ```haskell
 largestDivisible :: (Integral a) => a
 largestDivisible = head (filter p [100000, 99999..])
   where p x = x `mod` 3829 == 0
```


---
# takeWhile
#haskell/takeWhile
- it takes a predicate and a list and then goes from the beginning of the list and returns its elements while the predicate holds true
- once an element is found for which the predicate doesn't hold, it stops

-  If we wanted to get the first word of the string `"elephants know how to party"`, we could do `takeWhile (/=' ')` `"elephants know how to party" and it would return "elephants"`.


--------
# lambdas
it is anonymous function that is used because we need some functions only once


**to make a lambda**
`\ parm_1 parm_2 parm_n  ->  function body`

```haskell
numLongChains :: Int
numLongChains = length (filter (\xs -> length xs > 15) (map chain [1..100]))


map (\(a,b) -> a+b) [(1,2), (3,5), (6,3)]


```

-----------
# only folds and horses
a fold takes:
	- a binary function
	- a starting value/accumulator
	- a list to fold up

1. the binary function is called with the accumulator and the first (or last) element and produce a new accumulator
then
2. the binary function is called again with the new accumulator and the now new first (or last) element, 
3. and so on
we reduce the list to the value of accumulator

### `foldl` the left fold 
- it folds the list up from the left side
- the binary function is applied between the starting value and the head of the list
- that produces a new accumulator value and the binary function is called with that value and the nex element, etc

```haskell
sum'::(Num a) => [a] -> a
sum' xs = foldl (\acc x -> acc + x) 0 xs
sum' [3,5,2,1] -- -> 11
```
binary function: `\acc x -> acc + x`
the starting value: `0`
the list to be folded up: `xs`
1. `acc = 0` and `x=3`, so `0+3`=`3`, so `acc=3`
2. `acc=3` and `x=5`, so `3+5` = `8`, so `acc=8`
3. `acc=8` and `x=2`, ...

```haskell
sum''::(Num a) => [a] -> a
sum'' = foldl (+) 0
```
because:
- `(\acc x -> axx + x` is the same as `(+)`
- we can omit the `xs` because calling `foldl (+) 0` return a function that takes a list

> GENERALLY:
> `foo a = bar b a` you can rewrite it as `foo = bar b` because of curring

```haskell
elem' :: (Eq a) => a-> [a] -> Bool
elem' y ys = foldl (\acc x -> if x == y then True else acc) False ys
```
1. `acc=False`


## `foldr`
If we're mapping (+3) to [1,2,3]:
- we approach the list from the right side.
- We take the last element, which is 3 and apply the function to it, which ends up being 6. 
- Then, we prepend it to the accumulator, which is was []. 6:[] is [6] and that's now the accumulator. 
- We apply (+3) to 2, that's 5 and we prepend (:) it to the accumulator, so the accumulator is now [5,6]. 
- We apply (+3) to 1 and prepend that to the accumulator and so the end value is [4,5,6].
```haskell
map' :: (a->b) -> [a] -> [b]
map' f xs = foldr (\x acc -> f x : acc) [] xs
```


the same function with `foldl`
```haskell
map' f xs = foldl (\acc x -> acc ++ [f x]) [] xs
```

## ==`++` is more expensive than `:`==


## `foldl1` and `foldr1`
#haskell/foldl
- They are much like `foldl` and `foldr`, only you don't need to provide them with an explicit starting value
- they assime the first (last) element of the list to be the staerting value and then start the fold with the element nexto to it
```haskell
maximum' :: (Ord a) => [a] -> a  
maximum' = foldr1 (\x acc -> if x > acc then x else acc)  

reverse' :: [a] -> [a]  
reverse' = foldl (\acc x -> x : acc) []  

product' :: (Num a) => [a] -> a  
product' = foldr1 (*)  

filter' :: (a -> Bool) -> [a] -> [a]  
filter' p = foldr (\x acc ->  if p x then x : acc else acc) []  

head' :: [a] -> a  
head' = foldr1 (\x _ -> x)  

last' :: [a] -> a  
last' = foldl1 (\_ x -> x)
```


## `scanl` and `scanr`
#haskell/scan
They are like `foldl` and `foldr` only they report all the intermediate accumilator states in the form of a list

they are also `scanl1` and `scanr1`

```haskell
ghci> scanl (+) 0 [3,5,2,1]
[0,3,8,10,11]
ghci> foldl (+) 0 [3,5,2,1]
11
ghci>
```


# Funcion application with `$`
```haskell
($) :: (a -> b) -> a -> b  
f $ x = f x
```

Function aplication ==with a space== is **left-associative** (`f a b c`  the same `((f a ) b) c)`)

function application ==with `$`== is **right-associative**

`sum (map sqrt [1..130])`  -- the same --> 
`sum $ map sqrt [1..130]`


# Function composition
$$(f o )













