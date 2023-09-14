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

```python
from turtle import Turtle, Screen

tim = Turtle()
screen = Screen()

def move_foreward():
    tim.forward(10)
def move_backwards():
    tim.backward(10)

def turn_left():
    print(tim.heading())
    new_heading = tim.heading() + 10
    tim.setheading(new_heading)
  
def turn_right():
    print(tim.heading())
    new_heading = tim.heading() - 10
    tim.setheading(new_heading)

def clear():
    tim.clear()
    tim.penup()
    tim.home()
    tim.pendown()
  

screen.listen()
screen.onkey(key="w", fun=move_foreward)
screen.onkey(key="s", fun=move_backwards)
screen.onkey(key="a", fun=turn_right)
screen.onkey(key="d", fun=turn_left)
screen.onkey(key="c", fun=clear)

screen.exitonclick()
```

TURTLE RACE:

```python
from turtle import Turtle, Screen
import random

is_race_on = False
screen = Screen()
screen.setup(500,400) # set a size of the window
user_bet = screen.textinput("Choose color", "Write a color of a turtle that win the race: ")
print(user_bet)
colors = ["red", "green", "yellow", "purple", "blue", "orange"]
y_positions = [-80,-40,-0, 40, 80, 120]
all_turtles = []

for turtle_index in range(0,6):
    # tim = Turtle(shape="turtle")
    # tim.color(colors[turtle_index])
    # tim.penup()
    # tim.goto(x=-230,y=-y_positions[turtle_index])
    new_turtle = Turtle(shape="turtle")
    new_turtle.color(colors[turtle_index])
    new_turtle.penup()
    new_turtle.goto(x=-230,y=-y_positions[turtle_index])
    all_turtles.append(new_turtle)

  
if user_bet:
    is_race_on = True

while is_race_on:
    for turtle in all_turtles:
        if turtle.xcor() > 230:
            is_race_on =False
            winning_color = turtle.pencolor() # pencolor - the color of the turtle body
            if winning_color == user_bet:
                print(f"You've won!! THe {winning_color} turtle is the winner!")
            else:
                print(f"You've lost! The {winning_color} turtle is the winner!")

        random_distance = random.randint(0,10)
        turtle.forward(random_distance)

screen.exitonclick()
```







