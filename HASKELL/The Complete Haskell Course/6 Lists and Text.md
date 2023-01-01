# Definition
>[!info] List
>a list is a structured type that contains a sequence of elements, 
>==all of the same type==

```haskell
[]
[3,6,3] :: [Int]
[(1, 'a'), (21, "dwadzieścia jeden")] :: [(Int, String)]
[[8], [1,2,3], [1 .. 10]] :: [[Int]]
```



# List Constructors
Lists have two **constructors**
> `[]` 
> `[] :: [a]`

> and `:`:
> `(:) :: a -> [a] ->[a]`

`[15,12,21` is a shortcut for `15 : 12 : 21 : []` 
which means `15 : (12 : (21: []))`


Lists in Haskell are simply linked lists.
```haskell
l1 = 3:2:1:[]
l2 = 4:l1

-- 4->3->2->1->x
```

---
# Lists and Patterns
Pattern discrimination allows to decompose lists:
```haskell
sum [] = 0
sum (x:xs) = x + sum xs
```

### `list = head : tail`

> $e_1$ matches $e_2$ if there exists a subsitution for the variables of $e_1$ that make it the same as $e_2$
> examples:
> - `x:xs` matches `[2,5,8]` because you can substitute `x` by `2` and `xs` by `5: 8: []`
> - `x:xs` does not matche `[]`
> - `x1:x2:[]` matches `[2,5,8]` because `x1=2`,`x2=5`, `x=[8]`


---
# Syntax in Patterns
Pattern decomposition can also be used in the case `where` and `let`.
```haskell
sum list = 
	case list of
		[] -> 0
		x:xs -> x + sum xs

 divImod n m
	 | n < m = (0, n)
	 | otherwise = (q + 1, r)
	 where (q,r) = divImod (n-m) m

firstAndsecond list = 
	let first:second:rest = list
	in (first, second)
```


----
# Text
==Texts (strings) in Haskell are ;osts pf characters== 

`String` is a synonum of `[Char]` .
Double quates are syntactic sugar for defininf texts.

```haskell
name1 :: [Char]
name1 = 'j':'i':'m': []

name2 :: String
name2 = "jimael"
```


---
# Common Functions
```haskell
head :: [a] -> a
last :: [a] -> a

*Main> head [1..6]
1
*Main> last [1..6]
6
--------------------------------
tail :: [a] -> [a]
init :: [a] -> [a]
*Main> tail [1..4] -- the list without its first elem
[2,3,4] 
*Main> init [1..4] -- the list without its last elem
[1,2,3]
---------------------------
reverse :: [a] -> [a]
*Main> reverse [1..4]
[4,3,2,1] -- the list backwards
-------------------------------
length :: [a]-> Int
length []
0
length [1..5]
5
length "Angela"
6
----------------------
null :: [a] -> Bool
*Main> null [] -- is the list empty?
True -- 
*Main> null [1..5]
False
---------------------------------
-- elem x xs indicates if x is in the list xs
elem :: (Foldable t, Eq a) => a -> t a -> Bool
*Main> elem 6 [1..10]
True
*Main> 'k' `elem` "Dom"
False
--------------------------------------------
(!!) :: [a] -> Int -> a
*Main> ['a'..'f']
"abcdef"
*Main> ['a'..'f'] !! 2
'c'
---------------------------------------
*Main> :t (++)
(++) :: [a] -> [a] -> [a]
*Main> "JIM" ++ "My"
"JIMMy"
*Main> [1..5] ++ [1.3]
[1.0,2.0,3.0,4.0,5.0,1.3]

--------------
*Main> :t maximum
maximum :: (Foldable t, Ord a) => t a -> a

```














