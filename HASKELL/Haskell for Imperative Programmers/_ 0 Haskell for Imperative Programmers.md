https://www.youtube.com/watch?v=Vgu82wiiZ90&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV

#haskell #youtube 
#hagenlocher_philipp


# Functional Programming
- pure (mathematical) functions
- immutable date
- np/less side-effects
- declarative
- easier to verify
- lazy evaluation


# Functions 
https://www.youtube.com/watch?v=pitjnqRKyyI&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=2
## Definition

`name arg1 arg2 ... argn = <expression>`
`<expression>` - it is what the function returns

## Application
`name ar1 arg2 ... argn`

## Example
```haskell
in_range min max x = 
	x >= min && x <=max

in_range 0 5 3
True

in_range 4 5 3
False

```


# Types
Every value in Haskell has a type and that type is strict

```haskell
x :: Integer`
x = 1

y ::  Bool
y = True

z :: Float
z = 3.14154
```




