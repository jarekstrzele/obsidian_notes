
[[_ Deep Dive INTRO]]

[[Numeric Type]]
[[Rational Number]]

[[Floats 1]]

---

# DECIMAL
#python/decimal

another way to represent real numbers (alternative to usingfloat)

> __THE DECIMAL MODULE__ 
>                     `import decimal`


`float 0.1` :
- has infinite binary expansion
- has finite decimal expansion


Decimals have a context that controls certain aspects of working with decimals:
- __precision__ during arithmetic operations
- __rounding__ algorithm

this context can be _global_ -> the default context
			or temporary (_local_) -> sets temporary settings without affecting the global settings


`import decimal`
default context -> `decimal.getcontext()`
local context -> `decimal.localcontext(cts=None)` (returns a context manager)

`ctx = decimal.getcontext()` context (global in this case)
`ctx.prec` get or set the precision (value is an int)
`ctx.rounding` get or set the rounding mechanism (value is a string)

rounding algorithm:
- `ROUND_UP` rounds away from zero
- `ROUND_DOWN` rounds towards zero
- `ROUND_CEILING`
- `ROUND_FLOOR`
- `ROUND_HALF_UP` rounds to nearest, ties away from zero
- `ROUND_HALF_DOWN` rounds to nearest, ties towards zero
- `ROUND_HALE_EVEN` default (like in float) rounds to nearest, ties to even(least significant digit)

__GLOBAL__
`decimal.getcontext().rounding = decimal.ROUND_HALF_UP`

__LOCAL__
```python
with decimal.localcontext() as ctx:
	ctx.prec = 2
	ctx.rounding = decimal.ROUND_HALF_UP
```

```python
decimal.getcontext()
# ->

# Context(prec=28, rounding=ROUND_HALF_EVEN, Emin=-999999, Emax=999999, capitals=1, clamp=0, flags=[], traps=[InvalidOperation, DivisionByZero, Overflow])

type(decimal.getcontext()) #-> decimal.Context

decimal.localcontext() # -> <decimal.ContextManager at 0x7f3a59cf5970>

with decimal.localcontext() as ctx:
	ctx.prec = 6
	ctx.rounding = decimal.ROUND_HALF_UP
	print(ctx)

```





















