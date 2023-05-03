#python #tkinter #animation
[[_ 0 Python Tkinter GUI]]




```python
from tkinter import *

def move_up(event):
    lbl.place(x=lbl.winfo_x(), y=lbl.winfo_y()-5)

def move_down(event):
    lbl.place(x=lbl.winfo_x(), y=lbl.winfo_y()+5)

def move_left(event):
    lbl.place(x=lbl.winfo_x()-5, y=lbl.winfo_y())

def move_right(event):
    lbl.place(x=lbl.winfo_x()+5, y=lbl.winfo_y())

win=Tk()

win.geometry("500x500")
win.bind("<w>", move_up)
win.bind("<s>", move_down)
win.bind("<a>", move_left)
win.bind("<d>", move_right)
win.bind("<Up>", move_up)
win.bind("<Down>", move_down)
win.bind("<Left>", move_left)
win.bind("<Right>", move_right)

car_img = PhotoImage(file='car-blue.png')
lbl=Label(win, image=car_img)
lbl.place(x=0, y=0)

win.mainloop()
```