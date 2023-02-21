
[[_ Deep Dive INTRO]]

[[Numeric Type]]
[[Rational Number]]

---

[[Floats Coercing to Integers]]
[[Float Rounding]]

---

# Float
#python/float   #python/number 

>The `float` class is Python' s default implementation for representing real numbers.

- It is implemented using the `C double` type (`binary64`)
- it uses a __fixed__ number of bytes:
	- 8 bytes
	- 64 bits

Thes 64 bits are used up as folows:
- sign -> 1 bit
- exponent -> 11 bit (range[-1022,1023])
- significant digits -> 52 bits (15-17 siginificant (base-10) digits)
	- >__siginificant digits__ all digits except leading and trailing zeros   (1.2345 <- five significant digits;  1234.5 also five s.digits ; 1234500000 also five s.digits;  0.00012345 also five s.d.)  

---
## Representation: decimal
Numbers can be represented as base-10 integers and fractions:
$0.75 = \frac{7}{10}+\frac{5}{100} = 7*10^{-1} + 5 * 10^{-2}$ -> __2 significant digits__

$23.75 =20 +3 + \frac{7}{10}+\frac{5}{100} = 2*10^{1} + 3*10^{0} + 7*10^{-1} + 5 * 10^{-2}$ -> __3 significant digits__


In general:
$$
d=(-1)^{sign}\displaystyle\sum_{i=-m}^{n} d_{i}*10^{i}$$

$sign = 0$ for positive
$sign=1$ for negative


__some numbers cannot be represented using a finite number of terms__
$\pi=3.14159...$
$\sqrt{2}=1.4142..$
$\frac{1}{3} = 0.333333...$
...

---
## Representation: binary
Numbers in a computer are represented using bits, not decimal digits
so
instead of powers of 10, we need to use powers of 2
$$
(0.11)_{2} = (\frac{1}{2} + \frac{1}{4})_{10} =(1*2^{-1} + 1*2^{-2})_{10} = (0.75)_10
$$


In general:
$$
d=(-1)^{sign}\displaystyle\sum_{i=-m}^{n} d_{i}*2^{i}$$

$sign = 0$ for positive
$sign=1$ for negative


Some numbers that do have a finite decimal representation do not have a finite binary representation and some do

$(0.75)_{10} = (0.11)_{2}$ OK-finite
$(0.8125)_{10} = (0.1101)_{2}$ OK - finite

$(0.1)_{10} = (0 0011 0011 0011 ..)_{2}$ INFINITE - approximate

----
# Equality test problem

```py
a = 0.1 + 0.1 + 0.1
b = 0.3
print(a == b) # -> False

'a = {}'.format(a, '.25f') #a=0.30000000000000004 
'b = {}'.format(b, '.25f') #b=0.3
```

## how to solve that?
`round(a,5) == round(b, 5) # -> True`

### absolute tolerance
	more general:
for some $\epsilon > 0$, $a=b$ if and only if $|a-b| < \epsilon$

```py
def is_equal(x,y, eps):
	return math.fabs(x-y) < eps
```


### relative tolerance
using `%`  -> bigger tolerance for bigger number
`rel_tol = 0.001% = 0.00001 = 1e-5`
__relative__ to the larger magnitude of the two numbers
`tol = rel_tol * max(|x|, |y|)`

e.i.
```
x = 0.1 + 0.1 + 0.1
y = 0.3
# tol = 0.000003000000

a = 10000.1 + 10000.1 + 10000.1
b = 30000.3
# tol = 0.3000030000000
```

> Using a relative tolerance technique does not wor well for numbers close to zero!!!!!!!!!!!


SO COMBINE these to methods:
`tol = max(rel_to* max(|x|, |y|),  abs_tol)`

__the MATH module__ has that solution for us!!! `PEP 485`

`math.isclose(a,b, *, rel_tol=1e-09, abs_tol=0.0)`

```py
x = 123456789.01
y = 123456789.02
isclose(x,y)
#True

x = 0.01
y= 0.02
isclose(x,y)
# False

x = 0.01
y= 0.02
isclose(x,y, rel_tol=1)
# True
```


When a number is close to zero use the absolute tolerence (`abs_tol=0.01` as a arg in the `isclose` function)


