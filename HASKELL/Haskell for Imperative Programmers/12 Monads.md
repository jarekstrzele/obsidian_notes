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
```haksell
(>>=) :: Monad m => m a -> (a -> m b) -> m b
```
- we get a Monad of type `a` and functiom `m` to monad `b` and we get a monad `b`
- so get an internal type of the monad (e.g. `getLine` has its internal value - a string)
- so *bind* operator is able to extr





