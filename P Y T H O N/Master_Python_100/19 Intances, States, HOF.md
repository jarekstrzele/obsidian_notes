#python/hof
[[_ 0 100 Days of Code 2023]]

---

# First Event Listener
We need to be able to listen to things the user does (e.g. tap a key on the keyboard) - we need EVENTS LISTENERS

```python
from turtle import Turtle, Screen

tim = Turtle()
screen = Screen()

def move_foreward():
    tim.forward(10)

screen.listen()
screen.onkey(key="space", fun=move_foreward)

screen.exitonclick()
```

# HIGHER ORDER FUNCTIONS
Function as an input -> pass only the name of the function

```python
def fun1(fun2):
	pass

def fun2(fun1):
	pass
```
(make: `add(a,b,)`, `multiply(a,b)` functions and `calculate(a,b, fun)` that takes two parameters and a name of other function and returns the result of calling that function on these params) - `calculate` is a *higher order function*











