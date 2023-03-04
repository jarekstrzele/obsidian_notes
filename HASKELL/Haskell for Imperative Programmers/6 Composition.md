https://www.youtube.com/watch?v=dR_aUQXw5fs&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=8

[[_ 0 Haskell for Imperative Programmers]]
#haskell/composition


`(.) :: (b->c) -> (a->b) -> a -> c`
`(f . g)` equiv. to `(\x -> f (g x))`

```haskell

descSort = reverse . sort
descSort = (\x -> reverse(sort x))
descSort = reverse (sort x)
```

```haskell
map2D :: (a->b) -> [[a]] -> [[b]]
map2D = map . map
```

```haskell
($) :: (a->b)->a->b
f xs = map (\x -> x+1) (filter)
```













