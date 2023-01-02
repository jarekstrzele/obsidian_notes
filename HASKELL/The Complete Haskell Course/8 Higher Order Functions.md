>[!info] Higher Order Function
>It is a function that receives or returns functions
>**key point**: Functions are first-class objects

## Predefined functions

### `map`
```haskell
map :: (a->b) -> [a] -> [b]
map f [] = []
map f (x:xs) = f x : map f xs

map odd [1..5]
[True, False, True, False, True]
```

### `(.)` returns  the composition of two functions
```haskell
(.) :: (b->c) -> (a->b)->(a->c)
(f . g) x = f (g x)

(reverse . sort) [5, 3, 5, 2]
[5,5, 3, 2]
```


## other
```haskell
apli2 :: (a->a)->a->a
apli2 f x = f (f x)

apli2' :: (a->a) -> (a->a)
apli2' f = f . f

---------
*Main> apli2 sqrt 16.0
2.0
*Main> :r
[1 of 1] Compiling Main             ( text.hs, interpreted )
Ok, one module loaded.
*Main> apli2' sqrt 16
2.0
*Main> 

```


----------
# Anonymous Functions








