[[_ 0 Python Tkinter GUI]]

## read a file
```python
from tkinter import *
from tkinter import filedialog

win=Tk()

def file_open():
    # TextIOWrapper
    # file = filedialog.askopenfile()  # return a TextIOWrapper object  
    file_path = filedialog.askopenfilename(initialdir='C:\\Users\\jarek\\Downloads\\tech\\kalk',
        title="Open file", filetypes=(("text file", "*.txt"), ("all files", "*.*")) ) # sets a init dir
    # file_path = filedialog.askopenfilename()  # this function returns a string path
    # print(file_path)  
    # print(type(file))
    file = open(file_path, 'r')
    print(file.read())
    file.close()

btn=Button(text="O p e n", command=file_open)
btn.pack()

win.mainloop()
```


## write a file
```python
from tkinter import *
from tkinter import filedialog

win = Tk()
win.title("saver")

def saver():
    file=filedialog.asksaveasfile(defaultextension='.txt',
                                    filetypes=[
                                        ("Text file", '.txt'),
                                        ('HTML file', '.html'),
                                        ('All files', '.txt'),
                                    ],                                    initialdir="C:\\Users\\jarek\\Prog\\dyd"
    )

    if file is None:
        return
    fileText=str(text.get(1.0,END))
    file.write(fileText)
    file.close()


text = Text(win)
text.pack()

btn=Button(win, text="save", command=saver)
btn.pack()

win.mainloop()
```




