https://analityk.edu.pl/python-turtle-grafika-zolwia/





# Grafika żółwia
`import turtle`
```python
import turtle
 
t = turtle.Turtle()
t.shape('turtle')
 
turtle.exitonclick()
```

## podstawowe ruchy
```
forward(x)   fr(x)
backward(x)  bc(x)
right(x)     rt(x)
left(x)      lf(x)

goto(x,y)    idź do konkretnego punktu
home()        wróć na środek ekranu
circle(x)    narysuj koło o podanym promieniu

```


## kolory, rozmiar, prędkość

```
turtle.bgcolor(x) zmienia kolor tła, wartości: red, blue, greem, yellow, black, white (RGB(x,y,z))

color(x) zmiana koloru żółwia i jego linni
pensize(x) grubość linii

penup() bez rysowania
pendown() z rysowaniem

hideturtle()
showturtle()

speed(x) prędkość żółwia
write(x) żółw pisze tekst






```

```python
import turtle
import random
turtle.bgcolor('black')
t = turtle.Turtle()
t.speed(0)
for x in range(50, 300):
    t.color(random.choice(['white','red','blue','green','yellow']))
    t.forward(x)
    t.right(91)
 
turtle.exitonclick()
```


----
## Obsługa klawiszy
na końcu programu:
- `turtle.listen()`
- `turtle.mainloop()`

w programie
`turtle.onkey(funkcja, zdarzenie)`, czyli (co ma być zrobione, gdy wystąpi zdarzenie)

```python
import turtle
t = turtle.Turtle()
def up():
    t.forward(100)
def left():
    t.left(30)
def right():
    t.right(30)
def bye():
    turtle.bye()
turtle.onkey(up,'Up')
turtle.onkey(left,'Left')
turtle.onkey(right,'Right')
turtle.onkey(bye,'q')
turtle.listen()
turtle.mainloop()
```


























