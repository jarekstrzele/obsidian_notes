```python
from tkinter import *
from PIL import ImageTk, Image

def open_file():
    pass
def save_file():
    pass

win = Tk()
open_img=ImageTk.PhotoImage(Image.open('open.ico'))
save_img=PhotoImage(file='save.png')
exit_img=PhotoImage(file='exit.png')

menubar = Menu(win)

win.config(menu=menubar)

file_menu = Menu(menubar, tearoff=0)
menubar.add_cascade(label="File", menu=file_menu)
file_menu.add_command(label="Open", command=open_file,  image=open_img, compound='left')
file_menu.add_command(label="Save", command=save_file, image=save_img, compound='left')
file_menu.add_separator()
file_menu.add_command(label="Exit", command=quit, image=exit_img, compound='left')

edit_menu=Menu(menubar)
menubar.add_cascade(label="Edit", menu=edit_menu, font=("Arial", 12))
edit_menu.add_command(label="copy")
edit_menu.add_command(label="cut")
edit_menu.add_command(label="paste")


win.mainloop()
```