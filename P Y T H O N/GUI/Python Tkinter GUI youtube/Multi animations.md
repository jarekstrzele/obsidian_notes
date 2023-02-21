[[_ 0 Python Tkinter GUI]]

`main.py`
```python
import time
from tkinter import *
from ball import Ball

WIDTH = 500
HEIGHT = 500
  
win=Tk()

canvas= Canvas(win, width=WIDTH, height=HEIGHT)
canvas.pack()

volley_ball= Ball(canvas, 0,0,100,1,4,"white")
tennis_ball= Ball(canvas, 0,0,50,4,3,"green")
basket_ball= Ball(canvas, 0,0,23,2,4,"red")

while True:
    volley_ball.move()
    tennis_ball.move()
    basket_ball.move()
    win.update()
    time.sleep(0.01)

win.mainloop()
```


`ball.py`
```python
class Ball:
    def __init__(self, canvas, x, y, diameter, xVelocity, yVelocity, color):
        self.canvas = canvas
        self.image = canvas.create_oval(x,y,diameter, diameter, fill=color)
        self.xVelocity = xVelocity
        self.yVelocity = yVelocity

    def move(self):
        coords = self.canvas.coords(self.image)
        print(coords)
        if(coords[2]>=(self.canvas.winfo_width())) or coords[0]<0:
            self.xVelocity = -self.xVelocity
        if(coords[3]>=(self.canvas.winfo_height())) or coords[1]<0:
            self.yVelocity = -self.yVelocity
        self.canvas.move(self.image, self.xVelocity, self.yVelocity)
```
