[[_ 0 Python Tkinter GUI]]

#python #tkinter  #gui #listbox

It is a listing of selectable text items within it's own container

```python
from tkinter import *
from typing import List

win = Tk()

def submit():
   print("You have ordered")
   print(listbox.get(listbox.curselection()))

def add():
# listboxsize() -> current lenght of the listbox
   listbox.insert(listbox.size(), entryBox.get())
   listbox.config(height=listbox.size())

def delete():
# listboxsize() -> current lenght of the listbox
   listbox.delete(listbox.curselection())
   listbox.config(height=listbox.size())

listbox = Listbox(win, bg="#f7ffde", font=("Constantia", 35), width=12)
listbox.pack()

listbox.insert(1, "bug")
listbox.insert(2, "butterfly")
listbox.insert(3, "cockroach")
listbox.insert(4, "tapeworm")
listbox.insert(5, "beetle")

# dynamiczne ustawiania wielkości listbox
listbox.config(height=listbox.size())

entryBox = Entry(win)
entryBox.pack()

submit_btn=Button(win,text='submit', command=submit)
submit_btn.pack()

add_btn=Button(win, text="add", command=add)
add_btn.pack()

delete_btn=Button(win, text="delete", command=delete)
delete_btn.pack()

win.mainloop()
```

To select mutiple items:
Changes
```python
from tkinter import *
from typing import List

win = Tk()

def submit():
   food = []
   for index in listbox.curselection():
      food.insert(index, listbox.get(index))
      print("You have ordered")
      for item in food:
         print(item)

def add():
# listboxsize() -> current lenght of the listbox
   listbox.insert(listbox.size(), entryBox.get())
   listbox.config(height=listbox.size())

def delete():
   for index in reversed(listbox.curselection()):
      listbox.delete(index)

listbox = Listbox(win, bg="#f7ffde", font=("Constantia", 35), width=12, selectmode=MULTIPLE)

listbox.pack()
listbox.insert(1, "bug")
listbox.insert(2, "butterfly")
listbox.insert(3, "cockroach")
listbox.insert(4, "tapeworm")
listbox.insert(5, "beetle")

# dynamiczne ustawiania wielkości listbox
listbox.config(height=listbox.size())

entryBox = Entry(win)
entryBox.pack()

submit_btn=Button(win,text='submit', command=submit)
submit_btn.pack()

add_btn=Button(win, text="add", command=add)
add_btn.pack()

delete_btn=Button(win, text="delete", command=delete)
delete_btn.pack()

win.mainloop()
```





