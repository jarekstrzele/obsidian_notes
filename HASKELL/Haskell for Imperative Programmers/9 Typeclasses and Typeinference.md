https://www.youtube.com/watch?v=1txgSlcpQmo&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=13

#haskell/typeclasses

# Typeclasses

# Type constrain
```haskell
(+) :: Num a => a -> a -> a

```
`a`  has to have an **instance** of the `Num` typeclass

## Num typeclass
```bash
ghci> :info Num
type Num :: * -> Constraint
class Num a where
  (+) :: a -> a -> a
  (-) :: a -> a -> a
  (*) :: a -> a -> a
  negate :: a -> a
  abs :: a -> a
  signum :: a -> a
  fromInteger :: Integer -> a
```



## Show typeclass
```bash
ghci> :info Show
type Show :: * -> Constraint
class Show a where
  showsPrec :: Int -> a -> ShowS
  show :: a -> String
  showList :: [a] -> ShowS
  {-# MINIMAL showsPrec | show #-}
```



# Make an instance of a TypeClass
```haskell
data Temperature = C Float | F Float

instance Eq Temperature where
  (==) (C n) (C m) = n == m
  (==) (F n) (F m) = n == m
  (==) (C c) (F f) = (1.8*c + 32) == f
  (==) (F f) (C c) = (1.8*c + 32) == f
```

```haskell
data Temperature = C Float | F Float
	deriving (Show, Eq)o

-- derived equivalence - not good
instance Eq Temperature where
  (==) (C n) (C m) = n == m
  (==) (F n) (F m) = n == m
  (==) _ _ == false
```

----------
# Typeinference

algorithm
1. Assign every variable a unique typevariable
2. Assign every function its type with new unique typevariables
3. for each subexpression of the expression generate equations of types
4. Resolve the equations until no further simplifications can be done. Conflicting types imply a type error otherwise the type has been inferred


example:
```haskell
add x y z = (x + y) : z
```

ad. 1.  variables
```haskell
x :: a
y :: b
z :: c
```

ad. 2. functions
```haskell
(+) :: (Num d) => d -> d -> d
(:) :: e -> [e] -> [e]
```

ad. 3. equations
from `(x + y)` derive `a=d` and `b = d`
from `(x + y) : z` derive `[e] = c` and `d=e`

update:
```haskell
x :: d
y :: d
z :: [e]
z :: [d]
```

and the type is
```haskell
add :: (Num d) => d -> d -> [d] -> [d]
```


example
```haskell
f = reverse . sort
```

ad.2.
```haskell
reverse :: [a] -> [a]
(.) :: (c->d) -> (b->c) -> b -> d
sort :: Ord e => [e] -> [e]
```

ad.3.
from reverse . sort derive
`b = [e], c=[e], c=[a], d=[a]`


