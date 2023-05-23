
#haskell/folding

```haskell
foldr :: (a->b->b) -> b -> [a] ->b

```


`foldr :: (a->b->b)->b->[a]->b`

`foldr (#) a [x1,x2,...,xn] = x1 # x2 # ... # xn # a`

`a` accumulator/strting_value

`fold (+) 0 [1,2,...n] = 1 + 2+ ... +  n + 0`

with partial function ([[5 Partial Function Application and Currying]])
we can do:
```haskell
sum = foldr (+) 0
and = foldr (&&) True
or = foldr (||) False
```

with my own function
```haskell
foldr (\elem acc-> <term>) <start_acc> <list>


count e = foldr (\x acc -> if e == x then acc+1 else acc) 0


isAll e = foldr (\x -> (&&) $ e==x) True

isAll e = foldr (\x acc -> e==x && acc) True
```

```haskell
length = foldr (\x -> (+) 1) 0 -- we ignore the `x` 
-- or the same
length = foldr(const $ (+) 1) 0


map f = foldr ((:) . f) []
```

## Direction

```haskell
foldr (\elem acc -> <term>) <start_acc> <list>

foldl (\acc elem -> <term>) <start_acc> <list>
```

## Folding (Tree)


-------
# FOLD exercise

## Create a function `rev` that reverses a list
```haskell
-- Deklaracja funkcji
rev :: [a] -> [a]
rev = foldl (\acc x -> x: acc) []
-- Funkcja main
main :: IO ()
main = do
  print $ rev [1,2,3,4]
```
```
[1,2,3,4]
foldl(\[] 1 -> 1:[])
foldl(\[1] 2 -> 2:[1])
foldl(\[2,1] 3 -> 3:[2,1])
foldl(\[3,2,1] 4 -> 4:[3,2,1])
[4,3,2,1]
```


the same
```haskell

-- Deklaracja funkcji
rev :: [a] -> [a]
rev = foldl (flip (:)) []
-- Funkcja main
main :: IO ()
main = do
  print $ rev [1,2,3,4]
```

-----
Create a function **prefixes** that returns all the prefixes of a given list
```haskell
prefixes :: [a] -> [[a]]
-- prefixes [1,2,3] => [[1],[1,2], [1,2,3]]
-- Deklaracja funkcji
prefixes :: [a] -> [[a]]
prefixes = foldr (\x acc -> [x]: map (x:) acc) []
-- Funkcja main
main :: IO ()
main = do
  print $ prefixes [1,2,3,4]
  print $ map (+2) [10,20]
  print $ [2]: []
  print $ map (3:) [[1,2], [20,30,40]]

output
[[1],[1,2],[1,2,3],[1,2,3,4]]
[12,22]
[[2]]
[[3,1,2],[3,20,30,40]]
```

```
[1,2,3,4]
foldr (\1 [] -> [1]: map ((:) x) [] [1,2,3,4]
foldr (\2 [[1]] -> [1]: map ((:) x) [[1]] 
foldr (\1 [] -> [1]: map ((:) x) [] [1,2,3,4]
foldr (\1 [] -> [1]: map ((:) x) [] [1,2,3,4]
foldr (\1 [] -> [1]: map ((:) x) [] [1,2,3,4]

















