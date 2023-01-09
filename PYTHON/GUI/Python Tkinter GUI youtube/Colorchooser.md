
```python
from tkinter import *
from tkinter import colorchooser

win=Tk()
win.geometry("500x500")

def click():
    color = colorchooser.askcolor()
    # print(color) # -> e.g. ((105, 169, 216), '#69a9d8')
    colorHex=color[1]
    # print(colorHex)
    win.config(bg=colorHex)

btn=Button(win, text="Kliknij mnie", command=click)
btn.pack()

win.mainloop()
```