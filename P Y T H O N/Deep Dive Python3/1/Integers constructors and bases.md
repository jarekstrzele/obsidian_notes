[[_ Deep Dive INTRO]]

[[Integers]]


---
# Integers constructors and bases
- an integer number is an object - an instance of the `int` class
- the `int` class provides multiple contructor:
	- `a = int(10)`
	- `a = int(-10)`
	- `a = int(True)` -> a=1
	- `a = (Decimal("10.9")` -> a=10
	- `a = int("10")` -> $a=(10)_{10}$
		- __number base__ 2 <= base <= 36, default `base=10`
		- `int("1010", 2)` -> $(10)_{10}$ 
		- `int("A12F", base=16` -> $(41263)_10$
		- `int("a12f", base=16` -> $(41263)_{10}$
		- `int("A", base=11)` -> $(10)_{10}$

	__reverse__
	- `bin(10)` -> `0b1010`
	- `oct(10)` -> `0o12`
	- `hex(10)` -> `0xa`

you can write without stings: 
`a = 0b1010`
`a = 0o12`
`a = 0xA`

0..9, a..z -> 36 digits




---
# CODEs

```py
def from_base10(n,b):
  if n < 2:
    raise ValueError('Base b must be >=2')
  if n <0 :
    raise ValueError("Number n must be >= 0")
  if n ==0:
    return[0]
  digits = []
  while n > 0:
    # m, n = n %b, n //b
    n, m = divmod(n,b)
    digits.insert(0,m)
  return digits



```

```py
def encode(digits, digit_map):
  if max(digits) >= len(digit_map):
    raise ValueError("digit_map is not long enough to encode the digits")

	# for d in digits:
	#	encoding += digit_map[d]
	# retrun encoding
  return ''.join([digit_map[d] for d in digits])
```



















