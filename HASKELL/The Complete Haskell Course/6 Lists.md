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





























