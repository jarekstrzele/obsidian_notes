[[_ 0 Haskell for Imperative Programmers]]

https://www.youtube.com/watch?v=m12c99qgHBU&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=7

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
-- add 1 :: Int -> Int
-- add 1 returns (\y -> 1+y;)
```

`doubleList = map (\x -> x*2)` -> in returns a function that takes only one argument and that function we have written in the `doubleList`
`doubleList :: [a] -> [b]`







