
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

```haskell
data PeaNum = Succ PeaNum | Zero

incr :: PeaNum -> PeaNum
incr = Succ -- partial function

decr :: PeaNum -> PeaNum
decr (Succ n) = n
```

---
# Records
#haskell/records

## Constructor
```haskell
data Person = Persin {  name :: String,
						age  :: Int}
```

you get a function to get `name` and `age`
`name :: Person -> String `
`age :: Person -> Int `

```haskell
greet :: Person -> [Char]
greet person = "Hi " ++ name person

-- with pattern matching
greet (Person name _) = "Hi" ++ n
```


## Multiple Constructors
```haskell
data Point =
	  D2 {x :: Int, y :: Int}
	| D3 {x ::Int, y :: Int, z ::Int }

x (D2 1 2) => 1
x (D3 1 2 3) => 1
```
