[[0 - Haskell intro]]

>[!info] R E C U R S I O N
>It is a way of defining functions in which the function is applied inside its own definition

> **Recursion** is important to Haskell because unlike imperative languages, 
> 	- you do computations in Haskell by declaring what something _is_ instead of declaring _how_ you get it. 
> 	- That's why there are **no while loops or for loops in Haskell** and instead we many times have to use recursion to declare what something is.


## Maximum 
```haskell
maximum' :: (Ord a) => [a] -> a
-- max of singleton list is equal to the only element in it <-- AN EDGE CONDITION
-- max of a longer list is the head if the head is bigger than the max of the tail
-- if the max of the tailis bigger, thenit's the max
maximum' [] = error "maximum of empty list"
maximum' [x] = x
maximum' (x:xs)
  | x> maxTail = x
  | otherwise = maxTail
  where maxTail = maximum' xs

-- clearer way
max' :: (Ord a) => [a] -> a
max' [] = error "max of empty list"
max' [x] = x
max' (x:xs) = max x (max' xs)
```






