[[_ 0 Python Tkinter GUI]]


```python
from tkinter import *

def move_up(event):
   canvas.move(myImg, 0, -5)

def move_down(event):
    canvas.move(myImg, 0, 5)

def move_left(event):
    canvas.move(myImg, -5, 0)

def move_right(event):
    canvas.move(myImg, 5, 0)

win=Tk()
win.bind("<w>", move_up)
win.bind("<s>", move_down)
win.bind("<a>", move_left)
win.bind("<d>", move_right)
win.bind("<Up>", move_up)
win.bind("<Down>", move_down)
win.bind("<Left>", move_left)
win.bind("<Right>", move_right)
canvas = Canvas(win, width=500, height=500)
canvas.pack()

car_png = PhotoImage(file='car-blue.png')
myImg = canvas.create_image(0,0, image=car_png, anchor=NW)
  

win.mainloop()
```



