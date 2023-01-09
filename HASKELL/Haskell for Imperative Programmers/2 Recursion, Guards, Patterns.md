[[_ 0 Haskell for Imperative Programmers]]


# Recursion
`name <args> = ... name <args'>`

```haskell
fac n =
	if n <= 1 then 1
	else n * fac(n-1)
```



# Guards

```haskell
fac n
	| n <= 1 = 1
	| otherwise = n * fac (n-1)
```

guards are some boolean expressons
`otherwise` always eveluates to `True`


# Pattern Matching
```haskell
is_zero 0 = True
is_zero _ = False_
```










