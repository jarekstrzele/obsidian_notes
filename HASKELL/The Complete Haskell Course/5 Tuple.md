[[_ 0 Complete Haskell Course]]
#haskell/tuple

>[!info] tuple
>a tuple is a structure type that allows you to store different type values t1, t2, ... , tn on a single  value of type (t1, t2, ..., tn)
>- the number of fields is fixed
>- the fields are of heterogeneous type

```haskell
(3, 'z', False) :: (Int, Char, Bool)
(6,9)           :: (Int, Int)
(True, (6, 9))  :: (Bool, (Int, Int))

mostFrequentCharacter :: String -> (Char, Int)
mostFrequentCharacter "AVATAR"  
('A', 3)
```

```haskell
timeDecomposition :: Int -> (Int, Int, Int)

timeDecomposition seconds = (h, m, s)
	where
		h = div seconds 3600
		m = div (mod seconds 3600) 60
		s = mod seconds
```

## Access to Tuples

```haskell
fst :: (a, b) -> a

```

