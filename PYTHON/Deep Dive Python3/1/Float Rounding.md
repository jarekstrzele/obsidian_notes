[[_ Deep Dive INTRO]]

[[Floats 1]]
[[Float Rounding]]

---
# Float Rounding
`round(x, n=0)` a built-in rounding function
This will round the number `x` to the closest multiple of $10^{-n}$

`round(x)` -> `int`
`round(x), n ` -> same type as x
`round(x, 0) ` -> same type as x

$n=0$ round to the closest multiple of $10^{-0}=1$
`x=1.23` -> 1
this number is closer to 1 than to 2

$n=1$ round to the closest mulltiple of $10^{-1}=0.1$
`x=1.23` -> 1.2
this number is closet to 1.2 (0.03) then 1.3 (0.07)

$n=-1$ round to the closest mulltiple of $10^{-(-1)}=10$
`x=18.2` -> 20
this number is closet to 20 (1.8) then 10 (8.2)

## TIE
`x=1.25` -> ???
`round(1.25)` -> `1.2`
`round(1.35)` -> `1.4`

### BANKER's Rounding
>rounds to the nearest value, with ties rounded to the nearest value with an even least significant digit

`x=1.25` (it is between 1.2 and 1.3, `2` is even) -> `1.2`
`x=1.35`(it is between 1.3 and 1.4, `4` is even) -> `1.4`


`round(15,-1)` -> `20` ($15$ between $10$ and $20$, so $20$ is even)
`round(25,-1)` -> `20` ($25$ betweem $20$ and $30$, so $20$ is even)

> this banker's ropunding is less biased than ties away from zero
`0.5, 1.5, 2.5` $\rightarrow avg=4.5/3=1.5$
"Standard" rounding: `1, 2, 4` -> $6/3=2$
banker's rounding:  `0, 2, 2` -> $avg=4/3=1.3$
 
## roundign away from zero
`sign(x) *int(abs(x)+0.5)`
equivalent: `int(x + 0.5 * sign(x))`

but Python does not have a `sign` function.

`math.copysign(x, y)` returns the magnitude (absolute value) of `x` but with the `sign` of `y`

```python
def round_up(x):
	from math import copysign
	return int(x + copysign(0.5,x))
```

-----------
## example
```python
round(1.888, 3), round(1.8888, 2), round(1.8888, 1), round(1.8888,0)
# -> (1.888, 1.89, 1.9, 2.0)


round(888.88, 1), round(888.88, 0)
# -> (888.9, 889.0)

round(888.88, -1), round(888.88, -2), round(888.88, -3), round(888.88, -4)
# ->(890.0, 900.0, 1000.0, 0.0)

round(800, -4), round(9800, -4)
(0, 10000)
```











