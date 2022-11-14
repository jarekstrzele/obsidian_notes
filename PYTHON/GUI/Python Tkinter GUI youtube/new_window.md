#tkinter #window 

```python
from tkinter import *

win=Tk()

def create_window():
    new_win = Tk() # a new independent window or
                   # Toplevel() creates a new window depends on the main/bottom window

    win.destroy() # close out of the win window

Button(win, text="create new window", command=create_window).pack()

win.mainloop()
```

