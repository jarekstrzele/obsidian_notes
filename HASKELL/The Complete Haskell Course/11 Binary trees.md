#binary_tree 
# Fundamentals of Binary Trees

>[!info] Binary Tree
>data structure
>	- each node can have a left child and a right child
>	- they cannot have more than two children

common uses:
- binary search trees
- binary heaps
- Huffman coding
- 
## definition in Haskell
```haskell
data Bintree = Empty | Node Int Bintree
  deriving (Show)

-- to compute the height of the tree
height :: Bintree -> Int

Bintree Empty = 0
Bintree (Nome _ lc rc) = 1 + max (height lc) (height rc)
```


binary tree of generic data type
```haskell
data Bintree a = Empty | Node a (Bintree a) (Bintree a)
	deriving (Show)

t1 :: Bintree Int
t1 = Node 3 (Node 1 Empty Empty) (Node 2 Empty Empty)
```


---
# Problem 1 - Tree Size
`data Tree a = Node a (Tree a) (Tree a) | Empty deriving (Show)`

**size** - the nymber of node that the tree contains

```haskell
data Tree a = Node a (Tree a) (Tree a) | Empty
  deriving (Show)


size:: Tree a -> Int
size Empty = 0 -- Base Case: Emptry Tree
size (Node _ lc rc) = 1 + size lc + size rc

```

```haskell
ghci> let t7 = Node 7 Empty Empty
ghci> let t6 = Node 6 Empty Empty
ghci> let t5 = Node 5 Empty Empty
ghci> let t4 = Node 4 Empty Empty
ghci> let t3 = Node 3 t6 t7
ghci> let t2 = Node 2 t4 t5
ghci> let t1 = Node 1 t2 t3
ghci> size t1
7
```



















