[[Numeric Type]]
[[Integers]]


---
# Rational Number
#python/number 

>rational numbers are fractions of integer numbers
>any real number with a finite number of digits after the decimal point is also a rational number

$-\frac{22}{7}$

$0.45=\frac{45}{100}$

$\frac{8.3}{4}=\frac{83/10}{4}=\frac{83}{10}*\frac{1}{4}=\frac{83}{40}$


## The Fraction class
Rational number can be represented in Python using the ==Fraction class== in the ==fractions module==.

`from fractions import Fraction`
`x = Fraction(3,4)`
`y = Fraction(22,7)`

Fractions are automatically reduced:
`Fraction(6,10) -> Fraction(3,5)`


==Negative sign==, if any, is always attached to the numerator:
`Fraction(1,-4) -> Fraction(-1,4)`

###  Constractior
`Fraction(numerator=0, denominator=1)` by default
`Fraction(other_fraction)`
`Fraction(float)`
`Fraction(decimal)`
`Fraction(string)`
- `Fraction('10') -> Fraction(10,1)`
- `Fraction('0.125') -> Fraction(1,8)`
- `Fraction('22/7') -> Fraction(22,7)`


### Arithmetic operators
Standard arithmetic operators are suported
`+. -. *, /`
`Fraction(2,3) * Fraction(1,2) -> Fraction(1,3) `

```py
x = Fraction(22,7)
print(x.numerator) # -> 22
print(x.denominator) # -> 7
```


float objects finite precision, so
==any float object can be written as a fraction==

```py
import math
print(Fraction(math.pi)) 
# -> 884279719003555/281474976710656
# this is only an approximation!!!!!!
```

### CAVEAT
```py
print(Fraction(0.125)) # -> Fraction(1, 8) OK
print(Fraction(0.3)) # -> 5404319552844595/18014398509481984

```

###  Constraining the denominator
Given a Fraction object, we can find an approcimate equivalent fraction with a constrained denominator


```py
x = Fraction(math.pi)
print(x)
print(x.limit_denominator(10))
print(x.limit_denominator(100))
print(x.limit_denominator(1000))

# 884279719003555/281474976710656
# 22/7
# 311/99
# 355/113
```

