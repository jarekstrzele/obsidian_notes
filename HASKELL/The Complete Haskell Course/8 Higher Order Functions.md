>[!info] Higher Order Function
>It is a function that receives or returns functions
>**key point**: Functions are first-class objects


```haskell
map :: (a->b) -> [a] -> [b]
map f [] = []
map f (x:xs) = f x : map f xs

map odd [1..5]
[True, False, True, False, True]
```













