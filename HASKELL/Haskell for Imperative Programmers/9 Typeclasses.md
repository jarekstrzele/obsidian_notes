https://www.youtube.com/watch?v=1txgSlcpQmo&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=13

#haskell/typeclasses


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














