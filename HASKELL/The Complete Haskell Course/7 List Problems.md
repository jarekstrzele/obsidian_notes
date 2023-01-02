[[_ 0 Complete Haskell Course]]


# Last element
```Haskell
myLast :: [a] -> a

myLast :: [a]->a
myLast [] = error "Empty list"
myLast [x] = x
myLast (_:xs) = myLast xs
  
myLast2 :: [a] -> a
-- myLast2 x = head (reverse x)
-- the same:
myLast2 = head . reverse

------------
*Main> myLast2 [1,2,3]
3
*Main> myLast2 []
*** Exception: Prelude.head: empty list
*Main> myLast2 ["TOme" , "Jerry", "Tomorrow"]
"Tomorrow"
```

---
# Penultimate element

`myButLast :: [a] -> a`
`myButLast [1,2,3,4]` 
`3`
`myButLast ['a'..'z']`
`'y'`


```haskell
myButLast :: [a] -> a
myButLast :: [a]->a
myButLast [x,y] = x 
myButLast (_ : xs) = myButLast xs

myButLast2 :: [a] -> a
myButLast2 = head . tail . reverse
```

----
# Duplicate Elements

`dipli::[a]->[a]`
dupli [1,2,3]
[1,1,2,2,3,3]

```haskell
dupli :: [a]->[a]
dupli [] = []
dupli (x:xs) = x: x : dupli xs


```

---
# Average
average::[int]->Float
average [1,2,3] -> 2.0
average [8,1,3,9] -> 5.25















