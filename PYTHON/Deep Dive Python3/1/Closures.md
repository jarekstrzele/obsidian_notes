[[Scopes, closures, Decorators]]
[[Variable Scopes]]
[[Nonlocal Scope]]

[[Decorators 1]]

---

# Closures
#python/closure
(_closure_ zamknięcie, domknięcie, zakończyć)


Functions defined inside another function can access the outer (nonlocal variable).

`nonlocal` variable is called a ==free== variable

```py
def outer():
 x="python"

 def inner():
  print("{0} rocks!:.format(x))")

```
`x` is a free variable
when we consider `inner`, we really are looking at:
- the function `inner`
- the free variable `x` (with current value `python`)

`outer()` -> "python rocks!"  ==This is called a CLOSURE==
the function `inner` encloses the free variable `x`

---

## Returning the inner function
```py
def outer():
  x="python"
  
  def inner():
    print(f'{x} rocks!')

  return inner
```

`x` is a free variabke in `inner`
it is bound to the variable `x` in `outer`
this happens when `outer` runs (i.e. when `inner` is create)
this is the closure

`return inner` -> we are actually returning ==the closure== (`inner` + `the free variable - x`)

`fn=outer()` -> `fn` is that closure
`# after that outer is gone and its scope too!!!!`
but the `x` "exists" in the closure  `fn`
fn() -> "python rocks!"

---

## Python Cells and Multi-Scoped Variables

```py
def outer():    
  x="python"   # 'x' is shared between
               # two scopes:
               # outer
  def inner(): #
    print(x)

  return inner
```
lable/variable `x` is in two different scopes but always reference the same "value".

>Python does this by creating a cell as an intermediary object

==cell==  is a object that has a memory address
	  it contains a reference to another object


![[python_cell.excalidraw|800]]

both variables `x` (in `outer` and `inner`) point to the same cell
When requesting the value of the variable, Python will "double-hop" to get to the final value


>==CLOSURES== 
>You can think of the closure as a __function plus__ an extended scope that contains the free variables.
>==free variable's value== is the object the call points to 


Every time the function in the closure is called and the free variable is referenced --> Python looks up the cell object, and then whatever the cell is pointing to


![[python_closure.excalidraw|800]]

## INTROSPECTION
`fn.__code__.co_freevars` -> ('x',) 
(a is not a free variable)

`fn.__closure__` -> (<cell at 0x500: str object at 0xFF100>, )

---
## Modifying free variables

```py
def counter():
  count = 0

  def inc():
    nonlocal count # it is a free variable
    count += 1
    return count

  return inc


fn = counter()
fn() -> 1 # count's (indirect) reference changed from the object 0 to the object 1
fn() -> 2
```


## Multiple Instances of Closures
Every time we run a function, a new scope is created.
If that function generates a closure, a new closure is created every time as well.

The code above plus:
`f1=counter()` 
`f2=counter()`
-> two different closures!!


`n` is a global variable, so there are no closure
```py
adders = []
for n in range(1,4):
  adders.append(lambda x: x + n)

adders[0].__colsures__ $ -> nothing
```

but in this example `n` is a local variable, so there are three closures:
```py
def create_adders():
  adders = []
  for n in range(1,4):
    adders.append(lambda x: x+n)

  return adders # adders is a list of closures
```
==but n in all closures is equal to 3 BUG
adders[0](10) -> 13 but you expected 11==

To solve this problem you have to resignate from closures:
```py
def create_adders():
  adders = []
  for n in range(1,4):
    adders.append(lambda x, y=n: x+n)

  return adders

```
`y=x` the default value is set during creation, so `adders[0](10)` -> 11


---

## EXTENDED SCOPES CAN BE SHARED!!!!
but some time it can be misunderstandable
![[python_cell_value_shared.excalidraw|700]]

---


## NESTED CLOSURE
```py
def incrementer(n):
  # inner + n is a closure
  def inner(start):
    current = start
    # inc + current + n is a closure
    def inc():
      nonlocal current
      current += n
      return current

    return inc
  return inner

```
`
(inner)
`fn = incrementer(2)`  -> `fn.__code__.co_freevars` -> 'n' n=2

(inc)
`inc_2 = fn(100)` --> `inc_2.__code__.co_freevars` -> 'current' 'n'

(call inc)
`inc_2()` -> 102 (current = 102, n=2)
`inc_2()` -> 104 (current = 104, n=2)
...

---

## EXAMPLE apps

### first app - avg

```py
def average():
	total=0
	count=0

	def add(number):
		nonlocal total
		nonlocal count
		total = total + number
		count = count + 1

		return total/count

	return add
```

`a=average()`
`a(10)` -> 10
`a(20)` -> 15

### second app - timer

```py
from time import perf_counter

def timer():
	start = perf_counter()
	def poll():
		return perf_counter() - start

	return poll
```

`t2 = timer()`
`t2()` -> 4.32234


### third app - counter
```py
def counter(fn, counters):
  cnt = 0
  def inner(*args, **kwargs):
    nonlocal cnt 
    cnt += 1
    counters[fn.__name__] = cnt
    return fn(*args, **kwargs)

  return inner


c = dict()
counted_add = counter(add, c)
counted_mult = counter(mult, c)

counted_add(10,20)
counted_add(22,22)
counted_mult(12,29)

print(c) # -> {'add':2, 'mult': 1}
```







