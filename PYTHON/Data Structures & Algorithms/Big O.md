[[_Data Structures & Algorithms]]

---
# Big O
#big_o

https://www.bigocheatsheet.com/



> ==Big O== is a way of comparing two sets of code in, let's say, code on in code to accomplish exactly the same thing
> is a way of comparring code one in code to mathematically aboit how efficient they run


__time complexity__ it is not measured in time 
					it is measuered in the number of operations that it takes to complete something 

__space complexity__ (how many memory)

----

## Worse Case
Omega, Theta, omicrion Cron (big O)
$$
\varOmega

\Theta

\omicron
$$
	omega   - the best case scenario
	theta   - the average case scenario
	Omicron - the worst case scenario (`Big O`)

---

`O(n)`  - proportional (it needs `n` operations
)
```python
def print_items(n):
	for i in range(n):
		print(i)
```

---
## To simplfy
### Drop constants
```python
def print_items(n):
	for i in range(n):
		print(i)

	for j in range(n):
		print(j)
```

$n + n = 2n$
`O(2n)` -- drop the constant --> `O(n)`

### always squart
```python
def print_items(n):
	for i in range(n):
		for j in range(n):
			print(i,j)
```

$n*n=n^{2}$
$O(n^{2})$

```python
def print_items(n):
	for i in range(n):
		for j in range(n):
			for k in range(n):
				print(i,j,k)
```

$n*n*n=n^{3}$
$O(n^{3})$ -> $O(n^{2})$

### Drop Non-Dominants
```python
def print_items(n):
	for i in range(n):
		for j in range(n):
			print(i,j)

	for k in range(n):
		print(n)
```

$n*n + n=n^{2}+n$
$O(n^{2}+n)$
$n$ is non-dominant
so 
$O(n^{2}+n)$ -> $O(n^{2})$


### $O(1)$
contant time
```python
def add_items(n):
	return n+n
```
this is always one operation

```python
def add_items(n):
	return n+n+n
```

$O(2)$ -> $O(1)$       it's always contant time


### $O(log{\ } n)$
$2^{3}=8$
$log_2 8 =3$

very efficient

---
## Different Terms for Inputs

```python
def print_items(a,b):
	for i in range(a):
		print(i)
	for j in range(b):
		print(j)
```

wrong way: `O(a+b) = O(2n) = O(n)`
correct: `O(a) and O(b) so O(a+b)`

---
## LISTS
my_list.append(item) -> O(1)
my_list.pop() -> O(1)
my_list[11] -> O(1)

because we have to reindex
my_list.pop(0) -> O(n)
my_list.insert(0, item -> O(n)
my_list.insert(2,item) -> O(n)



---
## Wrap up
### O(n^2) Loop within a loop
### O(n) proportional
### O(log n) Divide and Conquer 
### O(1) constant
 





















