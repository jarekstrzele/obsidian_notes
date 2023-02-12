[[_ 0 Haskell for Imperative Programmers]]
#haskell/list 

https://www.youtube.com/watch?v=AN-P1-IvsKQ&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=4

#haskell/list  #haskell/tuple 

----
[[#Lists]]
[[#Tuples]]



---
# Lists
- only one type 
- contructor `[]`, `x:[]`
	- `[1,2,3]`, `1:2:3:[]`

```haskell
generateListAsc :: Int->Int->[Int]
generateListAsc n m
  | m < n = []
  | m == n =[m]
  | m > n = n : generateListAsc (n+1) m

-- ghci> generateListAsc 10 3
-- []
-- ghci> generateListAsc 3 10
-- [3,4,5,6,7,8,9,10]
-- ghci> generateListAsc 3 3
-- [3]
```


## `import Data.List`

## some functions

`head` -> first element
`tail` -> list without the first element

`length [10,20]` -> 2

`init` -> list without the last element


`null []` -> True
`null [1]` -> False

`and [True, False, True]` -> False
`or [True, False, True]` -> True

### list comprehension
`[2*x | x <- [1,2,3] ]` -> [2,3,6]
`[2*x | x <- [1,2,3], x > 1]` -> [4,6]
### `[<gen> | elem <-<list>, ..., <gurad>, ...]`
```haskell
ghci> [(x,y) | x <-[1,2,3,4], y<-['a','b'] ]
[(1,'a'),(1,'b'),(2,'a'),(2,'b'),(3,'a'),(3,'b'),(4,'a'),(4,'b')]
```

---------
# Tuples
- can have multiple types element
- 
```haskell
ghci> let (x,y) = (1,2) in x
1


addTuples :: [(Int, Int)] -> [Int]
addTuples xs = [x+y | (x,y) <- xs]
---
ghci> addTuples [(1,2), (2,3), (100,200)]
[3,5,300]

```


----
```haskell
--- Create a fun `elem` that returns True if element is in a given list and returns False otherwise

elem' :: (Eq a) => a -> [a] -> Bool
elem' _ [] = False
elem' x (y:ys)
  | x == y = True
  | otherwise = elem' x ys

elem2 :: (Eq a) => a -> [a] -> Bool
elem2 _ [] = False
elem2 e (x:xs) = (e == x)  || (elem e xs)




--- create a fun `nub` that removes all duplicates from a given list
nub :: (Eq a) => [a] -> [a]
nub [] = []
nub (x:xs)  
    | elem2 x xs = nub xs
    | otherwise = x : nub xs



```














