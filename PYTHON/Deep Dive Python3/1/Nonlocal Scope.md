[[Scopes, closures, Decorators]]
[[Variable Scopes]]



---


# Nonlocal Scope
We can define functions from inside another function:
```py
def outer_fnc():
	###

	def inner_fnc():
		###

	inner_fnc()


```

When we call `outer_func()`:
1. Pyhton creates a global scope,
2. Inside this scope Python create local scope (`outer_fnc`)
3. Inside this scope Python create local scope (`inner_fnc`)

> Both functions have access to the global and built-in scopes as well as their respective local scopes.


BUT the `inner` function also has access to its ==enclosing scopes== - the scope of the `outer` function!!!!!!!!!!!!!!!!
This scope is neither local not global - it is called a ==__NONLOCAL SCOPE__==


>We have to explicitly tell Python we are modifying a nonlocal variable `nonlocal` keyword


```py
def outer()
	x="hello"

	def inner1():
		def inner2():
			nonlocal x
			x = "python"
		inner2()
	
	inner1()

outer() # -> python
```

















