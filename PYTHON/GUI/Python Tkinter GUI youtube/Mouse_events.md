[[_ 0 Python Tkinter GUI]]


```python
from tkinter import *

win=Tk()
win.geometry("400x200")

def mouse_event_handler(event):
    #print("Button-3")
    print(f"Mouse coords: {event.x}, {event.y}")

# win.bind("<Button-1>", mouse_event_handler) # left button
# win.bind("<Button-2>", mouse_event_handler) # scroll
# win.bind("<Button-3>", mouse_event_handler) # right button
# win.bind("<ButtonRelease>", mouse_event_handler) # when button releases
# win.bind("<Enter>", mouse_event_handler) # a cursor enters a window
# win.bind("<Leave>", mouse_event_handler) # a cursor leaves a window

win.bind("<Motion>", mouse_event_handler) # active when a cursor is moving

win.mainloop()
```