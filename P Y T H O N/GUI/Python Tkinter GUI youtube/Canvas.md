[[_ 0 Python Tkinter GUI]]


widget that is used to draw graphs, plits, images in a window


```python
from tkinter import *

win = Tk()

canvas = Canvas(win, height=500, width=500)

# canvas.create_line(0,0, 500, 499, fill="blue", width=5)
# canvas.create_line(0,500, 500, 0, fill="green", width=5)
#canvas.create_rectangle(50,50,250,250, fill="purple")
# canvas.create_polygon(250,0,500,500,0,500,fill="purple", outline="gray", width=5)
# points = [250,0,500,500,0,500]
# canvas.create_polygon(points,fill="purple", outline="gray", width=5)
# canvas.create_arc(0,0,500,500, fill="purple", style=ARC) # style=CHORD, style=PIESLICE

canvas.create_arc(0,0,500,500, fill="red", extent=180, width=10) # 180, 270
canvas.create_arc(0,0,500,500, fill="white", extent=180, start=180, width=10) # 180, 270
canvas.create_oval(190,190,310,310, fill='white', width=10)
canvas.pack()
  

win.mainloop()
```

















