[[_ 0 Python Tkinter GUI]]

```python
import time

from tkinter import *

WIDTH = 400
HEIGHT = 400
xVelocity = 3
yVelocity = 2

win=Tk()

canvas = Canvas(win, width=WIDTH, height=HEIGHT)
canvas.pack()

bg_space_png = PhotoImage(file='space_bg.png')
my_bg = canvas.create_image(0,0, image=bg_space_png, anchor=NW)

ufo_png = PhotoImage(file='ufo_icon.png')
my_ufo_img = canvas.create_image(0,0, image=ufo_png, anchor=NW)

img_width = ufo_png.width()
img_height = ufo_png.height()
 

while True:
    coords = canvas.coords(my_ufo_img)
    print(coords)
    if (coords[0] >= (WIDTH - img_width) or coords[0]<0):
        xVelocity = -xVelocity
    if (coords[1] >= (HEIGHT - img_height) or coords[1]<0):
        yVelocity = -yVelocity
    canvas.move(my_ufo_img, xVelocity, yVelocity)
    win.update()
    time.sleep(0.01)
  

win.mainloop()
```



