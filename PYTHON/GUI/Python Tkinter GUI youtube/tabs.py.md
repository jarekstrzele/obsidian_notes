[[_ 0 Python Tkinter GUI]]


```python

from tkinter import *
from tkinter import ttk

win=Tk()

# widget that manages a collection of windows/displays
notebook = ttk.Notebook(win)

tab1 = Frame(notebook) # new frame for tab 1
tab2 = Frame(notebook) # new frame for tab2

notebook.add(tab1, text="tab 1")
notebook.add(tab2, text="tab 2")

# expand to fill any space not therwise used
# fill space on x and y axis ; value:x,y both
notebook.pack(expand=True, fill="both")

Label(tab1, text="Hello, this is tab#1", width=50, height=15).pack()
Label(tab2, text="Goodbye, this is tab#2", width=50, height=25).pack()

win.mainloop()
```






