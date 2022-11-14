[[Numeric Type]]


[[Integers constructors and bases]]

---

# INTEGERS
#python/number    #python/integer  

## How large can a Python `int` become(positive or negativ)?

Integers are represented internally using base-2 (binary) digits, not decimal.

$(10011)_2 = (19)_{10}$
Representing the decimal number 19 requires __5 bits__

8 bits (1 byte) to represent non-negative integers:
$2^8-1=255$

8 bits to represent positive and negative integers:
one bit to represent sign
$2^7-1=127$
$[-127,127]$

$0$ not require a sign, so
$[-128, 127]$
$[-2^7, 2^7-1]$

>in a 32-bit OS:
> memory spaces(bytes) are limited by  their address number:
> - 4,294,967,296 bytes of addressable memory
> - 4 GB


## `int` In Python
#python/integer

==The `int` object uses a variable number of bits!!!!==
Can use 4 bytes, 8 bytes, 12 bytes

lager number more memory
more memory slower standard operators (`+`, `*`, ...)

```py
import sys
sys.getsizeof(0) # -> 24 bits(?)
sys.getsizeof(1) # -> 160
```

---
### operations
- addition `+`           --> int
- subtraction `-`       --> int
- multiplication `*`     --> int
- ==division `/`           --> FLOAT!!!!!!!!!!==
- exponents `**`       --> int


TO MORE OPERATORS in integer arithmetic
- __FLOOR DIVISION__ (div) `//`
>the floor of real number `a` is the largest integer <= `a`
>$1.99=1$
>$-3.1=-4$
> 
$$
\frac{numerator}{denominator}
$$
$\frac{155}{4} = 38 + 3$
put another way:
$155 = 4 * 38 + 3 = 4*(155//4) + (155\%4)$
$155//4 = 38$
$155 \% 4=3$ 

- __MODULO__ operator (mod) `%`

these two operators always satisfy:
$$
n = d *(n // d) + (n \%d)
$$
n - numerator
d - denominator


positive number
```
a=135
b=4
135 / 4 = 33.75

135 // 4 -> 33
135 % 4 --> 3

4 *(135//4) + (135 % 4)= 4 * 33 + 3 = 132 + 3 = 135
```

negative number
```
a = -135
b = 4
-135 / 4 = -33.75

-135 // 4 -> -34
135 % 4 --> 1

4 *(-135//4) + (-135 % 4)= 4 * -34 + 1 = -136 + 1=135
```

---
example
```py
import math

print(math.floor(-3.000000000000001))  # -> -4
print(math.floor(-3.0000000000000001)) # -> -3

a=-33
b=16

print(math.floor(a/b)) # -> -3
print(math.trunc(a/b)) # -> -2

```







































