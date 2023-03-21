
```haskell
data Name = Constructor1 <args> | Constructor2 <args> | ...
```

examples
```haskell
data Color = Red | Orange | Yellow | Green | Blue | Magenta

data PeanNum = Succ PeanNum | Zero

data Calculation = Add Int Int | Sub Int Int | Mul Int Int | Div Int Int

```
`PeaNum` is recursuve

```haskell
calc :: Calculation -> Int
calc (Add x y) = x+y
calc (Sub x y) = x-y
calc (Mul x y )= x*y
calc (Div x y) = div x y
```


### Recursive data type with polimorphic type
```haskell
data Tree a = Leaf | Node (Tree a) a (Tree a)

tree :: Tree Int
tree = Node (Node Leaf 1 Leaf) 2 (Node (Node Leaf 3 Leaf) 4 Leaf)

```










