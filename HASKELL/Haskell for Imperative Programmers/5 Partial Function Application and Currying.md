
>[!info] partial function
>It is a result of so-called curring 


>[!info] curring
>it is a principle that tell us the following if we have a function that for example takes three args and return one value
>we could rewrite: 
>	function takes only a single argument and return function that again takes only one argument

```haskell
add :: Int -> Int -> Int
add x y = x+y
add x = (\y-> x+y)
add = (\x-> (\y -> x+y))

------------
add 1 -- it returns a new function
-- add
```





