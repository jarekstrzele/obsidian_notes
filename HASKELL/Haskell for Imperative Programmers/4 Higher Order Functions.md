#hof 
[[_ 0 Haskell for Imperative Programmers]]


HOF - function that takes a function as a argument 
```haskell
app :: (a->b) -> a -> b
app f x = f x

add1 :: Int -> Int
add1 x = x+1

app add1 1
2
```
## anonymous functions

`(\<args> -> <expr>)`

`add1 = (\x  -> x+1) 1` => 2

`(\x y z -> x+z+y) 1 2 3` => 6


## `map`
```haskell
map :: (a->b) -< [a] -> [b]

map (\(x,y) -> x+y) [(1,2), (2,3), (3,4)] -- =>[3,5,7]

```


## `filter`
```haskell
filter :: (a->Bool) -> [a] ->[a]

filter (\(x,y) -> x/= y) [(1,2), (2,2)] 
-- > [(1,2)]
```




















