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

















