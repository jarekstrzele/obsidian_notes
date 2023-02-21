[[_ Deep Dive INTRO]]

[[Numeric Type]]
[[Float - Internal Representations]]
[[Floats 1]]

---
[[Integers]]

# Floats Coercing to Integers
_coerce sb to sth_ zmuszać kogoś do czegoś
How we can coerce floats to integers?

`Floats -> Integers` __data loss__

Different ways of configure this data loss
- truncation
- floor
- ceiling
- rounding

## Truncation
>It returns the integer portion of the number i.e. ignores everything after the decimal point

```py
import math

math.trunc(10.4) # -> 10
math.trunc(10.9) # -> 10
math.trunc(-10.1) # -> 10
math.trunc(-10.6) # -> 10
```

### The `int` Constructor
The Python `int` constructor will accept a `float`.
We use __truncation__ when casting the `float` to an `int`.
```py
int(10.4) # -> 10
int(10.9) # -> 10
int(-10.1) # -> 10
int(-10.6) # -> 10
```


## Floor
$$
floor(x) = max\{i \epsilon Z | i <= x\}
$$
>the __floor__ of a number is the largest integer less then (or equal to) the number

$x=10.4->10$
$x=-10.4->-11$
For _positive_ numbers, floor and truncation are equivalent but NOT for NEGATIVE numbers
(see [[Integers#operations]])

```py
import math

math.foor(10.4)  # ->  10
math.floor(-10.4)# -> -11
```


## Ceiling
$$
ceil(x) = min\{i \epsilon Z | i <= x\}
$$
>the __ceiling__ of a number is the smallest integer greater then (or equal to) the number

```py
import math

math.ceil(10.4)  # ->  11
math.ceil(-10.4) # -> -10
 
```




















