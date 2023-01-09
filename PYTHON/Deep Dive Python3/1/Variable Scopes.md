[[Scopes, closures, Decorators]]





# Variable Scopes
#python/scope

---

NONLOCAL SCOPE: [[Nonlocal Scope]]

---

`a=10`
`a` points to object `10`
We say that the variable (name)(`a`) is ==bound== to that object (`10`).

That object can be accessed using that name in various parts of our code (__but not just anywhere!!!!!__).

>that variable name and it's binding (name and object) only "exist" in specific parts of our code;
>__lexical scope__ the portion of code where that name/binding is defined
>__namespace__ these bingins are stores in namespaces


## GLOBAL SCOPE
the global scope is essentially ==the module scope==.
It spans a single file only.

__exception__ the built-in globally objects such as `True False, None print ...`

![[python_global_scope.excalidraw|700]]






>If you reference a variable name inside a scope and Python does not find it in that scope's namespace it will look it in an enclosing scope's namespace


## LOCAL SCOPE
When we create functions, we can create variable names inside those functions(using assignments).

Variables definded inside a function are not created until the function is CALLED!!!!!!!!!!!!!!!!!!!!!
The scope will be created when the funtion will be called!!!!!!!!!!!
>Every time the function is called, a ==new scope is creates==!!!!!!!!


## NESTED SCOPES

>When retrieving the value of a global variable from inside a function, Python automatically searches the clocal scope's namespace, and up the chain of all enclosing scope namespaces

`local -> global -> built-in`

![[python_searching_scope.excalidraw|700]]


```py
a = 0
def my_fnc():
	a = 100
	print(a)
```

Python interprets `a=100` as a local variable (at compile-time); the local variable `a` ==masks== global variable `a` 

`global` ==keyword== we can tell Python that a variablle is meant to be scoped in the global scope by using the global keyword.

```py
def func(m):
	c = m **2
	return c

# c, m   are   local variables

```



### At complie-time
If a variable is assigned inside the function (without `global`), it will be local.

If a variable is not assigen inside the function, it will be non-local and Python will, at run-time, look for it in enclosing scopes.

```py
def fun():
	print(a)
	a=100
# there is a an assignment inside the function, so variable a will be local
# this function will generate an error in a run-time

```

INSIDE THE FUNCTION:
- the assignment -> local
- any assignment -> non-local


### FOR LOOP
```py
for i in range(10):
	x=2*i


print(x) # -> 18
print(i) # -> 9
```

















