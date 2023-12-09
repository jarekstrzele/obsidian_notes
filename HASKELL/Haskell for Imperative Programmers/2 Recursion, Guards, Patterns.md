[[_ 0 Haskell for Imperative Programmers]]

https://www.youtube.com/watch?v=y6xiaSkVlvs&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=3

#haskell/recursion

# Recursion
`name <args> = ... name <args'>`

```haskell
fac n =
	if n <= 1 then 1
	else n * fac(n-1)
```

## recursive with accumulators
```haskell
fac n = aux n 1
	where
		aux n acc
			| n <=1 = acc
			| otherwise = aux (n-1) (n*acc)
```
imperative version:
```haskell
fac n;
acc = 1;
while(True){
	if(n<=1){ 
		return acc 
	} else {
		n=n-1;
		acc=n*acc;	
	}
}
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










