[[_ 0 Python Tkinter GUI]]

You can bind: function+key+widget `widget_name.bind(event, function)`

### `window.bind("<Return>", do_something)`
`<Key>` any key

```python
from tkinter import *

win=Tk()
win.geometry("400x200")

def clicking(event):
    #print("you clicked a Return")
    #print("You tap: ", event.keysym)
    lbl.config(text=event.keysym)

#win.bind("<Return>", clicking)
win.bind("<Key>", clicking)

lbl=Label(win, font=("Helvetiva", 70))
lbl.pack()

win.mainloop()
```
















