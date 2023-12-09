#monad

# Monad definition

```bash
type Monad :: (* -> *) -> Constraint
class Applicative m => Monad m where
  (>>=) :: m a -> (a -> m b) -> m b
  (>>) :: m a -> m b -> m b
  return :: a -> m a
  {-# MINIMAL (>>=) #-}
  	-- Defined in ‘GHC.Base’
instance Monad (Either e) -- Defined in ‘Data.Either’
instance Monad [] -- Defined in ‘GHC.Base’
instance Monad Solo -- Defined in ‘GHC.Base’
instance Monad Maybe -- Defined in ‘GHC.Base’
instance Monad IO -- Defined in ‘GHC.Base’
instance Monad ((->) r) -- Defined in ‘GHC.Base’
instance (Monoid a, Monoid b, Monoid c) => Monad ((,,,) a b c)
  -- Defined in ‘GHC.Base’
instance (Monoid a, Monoid b) => Monad ((,,) a b)
  -- Defined in ‘GHC.Base’
instance Monoid a => Monad ((,) a) -- Defined in ‘GHC.Base’

```

only ONE function that we need to have
`  {-# MINIMAL (>>=) #-}`

`Maybe`, `IO` are monads
instance Monad Maybe -- Defined in ‘GHC.Base’
instance Monad IO -- Defined in ‘GHC.Base’

---
# `>>=` (bind)
a bind operator  returns a monad

```haksell
(>>=) :: Monad m => m a -> (a -> m b) -> m b
```
- we get a Monad of type `a` and functiom `m` to monad `b` and we get a monad `b`
- so get an internal type of the monad (e.g. `getLine` has its internal value - a string)
- so *bind* operator is able to *extract* that *value*
```haskell
Just 1 >>= (\x -> Just x) ==> Just 1
Nothing >>= (\x -> Just x) ==> Nothing
```


example
```haskell
maybeadd :: Num b => Maybe b -> b -> Maybe b
maybeadd mx y = mx >>= (\x -> Just $ x+y)

maybeadd Nothing 1 ==> Nothing
maybeadd (just 1) 1 ==> Just 2
```

```haskell
maybeadd :: Num b => Maybe b -> Maybe b -< Maybe b
maybeadd mx my = mx >>= (\x -> my >>= (\y -> Just $ x+y))

maybeadd Nothing (Just 1) ===> Nothing
maybeadd (Just 2) (Just 1) ===> Just 3

```

### `return`
`return` should take a value and then return the monad of that value
```haskell
maybeadd :: (Monad m, Num b) => m b -> m b -< m b
maybeadd mx my = mx >>= (\x -> my >>= (\y - return $ x+y))
```



















