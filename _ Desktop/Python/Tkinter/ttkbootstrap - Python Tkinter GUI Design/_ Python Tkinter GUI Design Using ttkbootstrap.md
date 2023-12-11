#youtube #freecodecamp  #python #tkinter #gui 

https://www.youtube.com/watch?v=0tM-l_ZsxjU&t=2s

https://ttkbootstrap.readthedocs.io/en/latest/

---------









-------
# Install 

##### `python -m pip install ttkbootstrap`


---
# First app label, button, style
```python
from tkinter import *
from ttkbootstrap.constants import * #e.g. DEFAULT
import ttkbootstrap as tb
  

root = tb.Window(themename="superhero") # see theme on the  ttkbootstrap web
  

root.title("TTK Bootstrap!")
root.geometry("500x500")

is_clicked = False
def on_click():
    global is_clicked
    if not is_clicked:
        my_label.config(text="Coś się zmieniło!")
        is_clicked = True
    else:
        my_label.config(text="Nic się nie zmieniło!")
        is_clicked = False
  

# Colors  from bootstrap --> see style guide on the ttkbootstrap web
# default, primary, secondary, success, info, warning, danger, light, dark
my_label = tb.Label(text="Start", font=("Helverica", 28), bootstyle=(DEFAULT, INVERSE))
my_label.pack(pady=50)

my_button = tb.Button(text="Naciśnij mnie", bootstyle="success, outline", command=on_click)
my_button.pack(pady=20)

root.mainloop()
```


---------
# checkbutton

```python
from tkinter import *
from ttkbootstrap.constants import * #e.g. DEFAULT
import ttkbootstrap as tb

root = tb.Window(themename="cyborg") # see theme on the  ttkbootstrap web

root.title("TTK Bootstrap!")
root.geometry("500x500")

is_clicked = False
def on_click():
    global is_clicked
    if not is_clicked:
        my_label.config(text="Coś się zmieniło!")
        is_clicked = True
    else:
        my_label.config(text="Nic się nie zmieniło!")
        is_clicked = False

# Colors  from bootstrap --> see style guide on the ttkbootstrap web

# default, primary, secondary, success, info, warning, danger, light, dark

my_label = tb.Label(text="Do you want to sell your kidney?", font=("Arial", 18), bootstyle="waring")

my_label.pack(pady=(30,10))

  

def checker():

    if is_check.get() == 1:

        my_label.config(text="You want to sell your kidney!!!!!")

    else:

        my_label.config(text="You don't want to do it!!! :(")

is_check = IntVar()

# onvalue i offvalue są opcjonalne, domyślnie są przekazywane 1, 0,

# ich wartości zostaną przekazane do obiektu IntVar()

my_check = tb.Checkbutton(bootstyle="waring", text="Yes, I do!",  variable=is_check, onvalue=1, offvalue=0, command=checker)

my_check.pack(pady=(20,10)) # 40 pikseli od góry, 10 pikseli od dołu

  
  

# TOOLBUTTON

var_tool2 = IntVar()

def checker2():

    print(var_tool2.get())

    if var_tool2.get() == 10:

        tool_label.config(text="You are sure!!!")

    else:

        tool_label.config(text="You are  not sure!!")

my_tool_button = tb.Checkbutton(bootstyle="danger, toolbutton", text="It's your destiny",  variable=var_tool2, onvalue=10, offvalue=20, command=checker2)

my_tool_button.pack(pady=(20,10), padx=(30,10)) # 40 pikseli od góry, 10 pikseli od dołu

tool_label = tb.Label(text="Are you sure?", font=("Arial", 18), bootstyle="danger")

tool_label.pack( pady=(10,20), padx=(40,40))

  

var_tool3 = IntVar()

def checker3():

    if var_tool3.get() == 1:

        tool_label3.config(text="No tak")

    else:

        tool_label3.config(text="No nie")

my_tool_button3 = tb.Checkbutton(bootstyle="info, toolbutton, outline", text="Other possiblity",  variable=var_tool3, command=checker3)

my_tool_button3.pack(pady=(20)) # 40 pikseli od góry, 10 pikseli od dołu

tool_label3 = tb.Label(text="No tak", font=("Helverica", 18), bootstyle="info")

tool_label3.pack(pady=(10))

  

# round Toggle Button

var_tool4 = IntVar()

def checker4():

   print(var_tool4.get())

   if var_tool4.get() == 1:

       root.geometry("800x500")

   else:

       root.geometry("500x500")

my_tool_button4 = tb.Checkbutton(bootstyle="success, round-toggle", text="Bigger window",

                                  variable=var_tool4,

                                  onvalue=1,

                                  offvalue=0,

                                  command=checker4)

my_tool_button4.pack(pady=(20)) # 40 pikseli od góry, 10 pikseli od dołu

  

# round Toggle Button

var_tool5 = IntVar()

def checker5():

   print(var_tool5.get())

   if var_tool5.get() == 1:

       root.geometry("200x500")

   else:

       root.geometry("500x500")

my_tool_button5 = tb.Checkbutton(bootstyle="secondary, square-toggle", text="smaller square window",

                                  variable=var_tool5,

                                  onvalue=1,

                                  offvalue=0,

                                  command=checker5)

my_tool_button5.pack(pady=(20)) # 40 pikseli od góry, 10 pikseli od dołu

  

root.mainloop()
```

------------------
# Resizing button

https://www.youtube.com/watch?v=0tM-l_ZsxjU&t=2s














