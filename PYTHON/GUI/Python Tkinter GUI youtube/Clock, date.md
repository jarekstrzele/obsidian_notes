[[_ 0 Python Tkinter GUI]]


```python
from tkinter import *
from time import *

def update():
    time_str=strftime("%I:%M:%S %p")
    time_lbl.config(text=time_str)
  
    day_str=strftime("%A")
    day_lbl.config(text=day_str)

    date_str=strftime("%B %d, %Y")
    date_lbl.config(text=date_str)

    # time_lbl.after(1000, update)
    win.after(1000, update)

win=Tk()

time_lbl = Label(win, font=("Symbol", 50), fg="#FFE381", bg="#1C448E")
time_lbl.pack()

day_lbl = Label(win, font=("Cambria", 25), bg="#DBFE87", fg="#6F8695")
day_lbl.pack(fill=BOTH)

date_lbl = Label(win, font=("Cambria", 15), bg="#FFE381", fg="#6F8695")
date_lbl.pack(fill=BOTH)

update()

win.mainloop()
```