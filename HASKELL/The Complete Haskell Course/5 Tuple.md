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
		s = mod seconds 60
```

## Access to Tuples

```haskell
fst :: (a, b) -> a
snd :: (a, b) -> b
```

```haskell
first (x, _, _) = x
third (_,_, z) = z
```


## Decomposition fo Tuples into Patterns
```haskell
distance p1 p2 = sqrt (sqr dx + sqr dy)
	where 
		(x1, y1) = p1
		(x2, y2) = p2
		dx = x1-x2
		dy = y1-y2
		sqr x = x * x
```

```haskell
distance (x1, y1) (x2, y2) = sqrt ((x1 -x2)^2 + (y1-y2)^2)
```

## Empty Tuple (Unit)
There exists the tuple type without any data, which has only one possible value: the empty data.
















