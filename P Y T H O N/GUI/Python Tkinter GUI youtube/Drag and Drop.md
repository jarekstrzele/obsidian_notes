[[_ 0 Python Tkinter GUI]]

oop with one object
```python
from tkinter import *

class Main(Tk):
    def __init__(self, size="400x400", title="Nowe puste okno"):
        super().__init__()
        self.geometry(size)
        self.title(title)
    def start(self):
        super().mainloop()

class App(Frame):
    def __init__(self, master):
        super().__init__(master)
        self.grid()
        self.create_widgets(master)

    def drag_start(self, event):
        self.lbl.startX = event.x
        self.lbl.startY = event.y

    def drag_motion(self, event):
        #widget = event.widget
        x = self.lbl.winfo_x() - self.lbl.startX + event.x
        y = self.lbl.winfo_y() - self.lbl.startY + event.y
        self.lbl.place(x=x, y=y)

    def create_widgets(self, master):
        self.lbl=Label(master, bg="red", width=10, height=5)
        self.lbl.place(x=0, y=0)
        self.lbl.bind("<Button-1>", self.drag_start)
        self.lbl.bind("<B1-Motion>", self.drag_motion)

if __name__ == '__main__':
    win = Main(title='drag and drop')
    app = App(win)
    win.start()
```

oop more than one object
```python
from tkinter import *

class Main(Tk):
    def __init__(self, size="400x400", title="Nowe puste okno"):
        super().__init__()
        self.geometry(size)
        self.title(title)

    def start(self):
        super().mainloop()

class App(Frame):
    def __init__(self, master):
        super().__init__(master)
        self.grid()
        self.create_widgets(master)

    def create_widgets(self, master):
        self.lbl=Square(master, bg="red", width=10, height=5, x= 10, y=5)
        self.lbl=Square(master, bg="green", width=10, height=5, x= 10, y=5)

class Square(Label):
    def __init__(self, master, bg="red", width=10, height=5, x=0, y=0):
        super().__init__(master, bg=bg, width=width, height=height )
        self.place(x=x, y=y)
        self.bind("<Button-1>", self.drag_start)
        self.bind("<B1-Motion>", self.drag_motion)

    def drag_start(self, event):
        self.startX = event.x
        self.startY = event.y

    def drag_motion(self, event):
        x = self.winfo_x() - self.startX + event.x
        y = self.winfo_y() - self.startY + event.y
        self.place(x=x, y=y)

  
if __name__ == '__main__':
    win = Main(title='drag and drop')
    app = App(win)
    win.start()
```

with one object:
```python
from tkinter import *

win = Tk()
win.title("drag and drop")
win.geometry("400x400")

def drag_start(event):
    lbl.startX = event.x
    print(lbl.startX)
    lbl.startY = event.y
    print(lbl.startY)

def drag_motion(event):
    x = lbl.winfo_x() - lbl.startX + event.x
    y = lbl.winfo_y() - lbl.startY + event.y
    print(f'x={x}, y={y}')
    lbl.place(x=x, y=y)

lbl=Label(win, bg="red", width=10, height=5)
lbl.place(x=0, y=0)

lbl.bind("<Button-1>", drag_start)
lbl.bind("<B1-Motion>", drag_motion)

win.mainloop()
```

with two or more object
```python
from tkinter import *

win = Tk()
win.title("drag and drop")
win.geometry("400x400")

def drag_start(event):
    widget = event.widget
    widget.startX = event.x
    widget.startY = event.y
def drag_motion(event):
    widget = event.widget
    x = widget.winfo_x() - widget.startX + event.x
    y = widget.winfo_y() - widget.startY + event.y
    widget.place(x=x, y=y)

lbl=Label(win, bg="red", width=10, height=5)
lbl.place(x=0, y=0)
lbl.bind("<Button-1>", drag_start)
lbl.bind("<B1-Motion>", drag_motion)

lbl2=Label(win, bg="green", width=10, height=5)
lbl2.place(x=100, y=200)
lbl2.bind("<Button-1>", drag_start)
lbl2.bind("<B1-Motion>", drag_motion)

win.mainloop()
```




