[[0 - Haskell intro]]

---

# Haskell lists
#haskell/list 

__lists__  the most used data structure in Haskell
__list__ is:
- _homogenous_ data structure (it stores several elements od the same type)
- in _GHCI_ use `'let variable_name'` in a script use `variable_name`

`string` is just list of characters
```haskell
ghci> let b = [[1], [1,2], [1,2,3]]
ghci> b
[[1],[1,2],[1,2,3]]

```


```haskell
let nums = [1,2,4,5]

-- [1, 2 , 3] + [20,12]
-- "hello" ++ " " ++ "world"
ghci> "Tom " ++ "and " ++ " Jerry"
"Tom and  Jerry"

-- add element at the beginning of a list:
ghci> 'a' : " small cat"
"a small cat"

ghci> 1: [40,50,60] 
[1,40,50,60]

ghci> 1:2:3:[]
[1,2,3]

```


__to use index__
`!!`
```haskell
ghci> "Tomek pije mleko" !! 4
'k'

```


__to compare lists__
`>   >=   <   <=`
the are compard in lexicographical order. First the heads are compared. If they are equal then the second elements are compared, ...
```haskel
ghci> [3,2,1] > [2,1,0]
True
ghci> [2,10,0] > [3,11,1]
False

```


## basic functions that operate on lists
#haskell/head #haskell/tail #haskell/last #haskell/init
```haskell
ghci> head [1,2,3,4,5]
1
ghci> tail [1,2,3,4,5]
[2,3,4,5]
ghci> last [1,2,3,4,5]
5
ghci> init [1,2,3,4,5]
[1,2,3,4]

ghci> head []
*** Exception: Prelude.head: empty list

```

#haskell/null   #haskell/length   #haskell/reverse

```haskell
ghci> length [1,2,3]
3
ghci> null [1,2,3]
False
ghci> null []
True
ghci> reverse [1,2,3]
[3,2,1]
ghci> take 3 [1,2,3,4,5]
[1,2,3]
ghci> take 0 [1,2,3,4,5]
[]

```
use `null` instead of `xs==[]` ('xs' is a name of a list)

#haskell/drop    #haskell/take
```haskell
ghci> take 3 [1,2,3,4,5]
[1,2,3]
ghci> take 0 [1,2,3,4,5]
[]
ghci> drop 3 [1,2,3,4,5]
[4,5]
ghci> drop 2 [1,2,3,4,5]
[3,4,5]
ghci> drop 3 []
[]
ghci> drop 100 [1,2,3,4,5]
[]

```

`take` extracts that many elements from the BEGINNING of the list
`drop` drops the number of elements from the begining of a list

`maximum`
`minimum`
`sum` takes a list of numbers and returns their sum
`product` takes a list of numbers and returns their product
`elem` (an infix function) takes a thind a list of things and tells us if that thing is an element of the list
```haskell
ghci> 4 `elem` [2,3,4,5]
True
ghci> 4 `elem` [2,3,5]
False

```

## Texas ranges
```haskell
ghci> [1..20]
[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20]
ghci> ['a'..'k']
"abcdefghijk"

ghci> [20, 19..1]
[20,19,18,17,16,15,14,13,12,11,10,9,8,7,6,5,4,3,2,1]
ghci> [20, 18..1]
[20,18,16,14,12,10,8,6,4,2]

ghci> take 24 [13,26 ..]
[13,26,39,52,65,78,91,104,117,130,143,156,169,182,195,208,221,234,247,260,273,286,299,312]

```


`cycle` __takes a list__ and cycles it into an INFINITE list
```haskell
ghci> take 12 (cycle " lol")
" lol lol lol"

ghci> take 10 (cycle [1,2,3])
[1,2,3,1,2,3,1,2,3,1]

```

`repeat` __takes an element__ and produces an infinite list of just that element
```haskell
ghci> take 10 (repeat 5)
[5,5,5,5,5,5,5,5,5,5]

```

## a list comprehension


`[elem | elem <- from, predicate1, ...]`
```haskell
ghci> [x*2 | x <- [1..10]]
[2,4,6,8,10,12,14,16,18,20]

ghci> [x*2 | x <- [1..10], x*2 >= 12]
[12,14,16,18,20]

ghci> [x*2 | x <- [50..100], x `mod` 7 == 3]
[104,118,132,146,160,174,188]
```


`[elem | elem <- from, elem1 <-from, pred1, ...]`
```haskell
ghci> [x ++ y | x<- ["2", "5","10"], y <-["8","10","11"]]
["28","210","211","58","510","511","108","1010","1011"]
ghci> [x*y | x<- [2,5,10], y <-[8,10,11]]
[16,20,22,40,50,55,80,100,110]
ghci> 

```

The function that replaces every elemtn of  a list with *1* and the sums that up:
`length' xs = sum[1 | _ <- xs]`
`_` we don't care what we'll draw from the list 







