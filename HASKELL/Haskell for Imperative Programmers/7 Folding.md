`foldr :: (a->b->b)->b->[a]->b`

`foldr (#) a [x1,x2,...,xn] = x1 # x2 # ... # xn # a`

`a` accumulator/strting_value

`fold (+) 0 [1,2,...n] = 1 + 2+ ... +  n + 0`

with partial function ([[5 Partial Function Application and Currying]])
we can do:
```haskell
sum = foldr (+) 0
and = foldr (&&) True
or = foldr (||) False
```

with my own function
```haskell
foldr (\elem acc-> <term>) <start_acc> <list>


count e = foldr (\x acc -> if e == x then acc+1 else acc) 0


isAll e = foldr (\x -> (&&) $ e==x) True

isAll e = foldr (\x acc -> e==x && acc) True



```










