#python #gui #tkinter


https://docs.python.org/3/library/tk.html


# Tkinter 0
```python
from tkinter import Tk, Label, Button, Entry

window = Tk()
window.title("fowfjweoifjwf")
window.minsize(width=500,height=300)
  

# Label
my_lbl = Label(text="I am a label", font=("Arial", 24, "bold"))
my_lbl.place(x=100,y=100) # dokleja do okna i centruje
my_lbl["text"] = "New tekst"
my_lbl.config(text="New texttttt")
  

def btn_clicked():
	my_lbl.config(text=input.get())
#button
btn = Button(text="CLick Me", command=btn_clicked)
btn.pack()

# Entry
input = Entry(width=10)
input.pack()

window.mainloop()
```

# Tkinter Layout Managers
Widżet będzie widoczny tylko wtedy, gdy zostanie na nim uruchomiany jakiś manager układu (*layout manager*)
## pack()
- "pakuje"  widżety obok siebie obok każdy
- domyślnie zaczyna od góry i środka, a każdy kolejny umieszcza pod poprzednikiem
- `side=`:left, right, to, down

## place()
- dokładne pozycjonowanie przez podawanie współrzędnych
- `my_lbl.place(x=0, y=100)`


# grid()
==niekompatynbilne: grid + pack!!!==
`grid(column=0, row=0)`
- cały program to siatka, która będzie miała tyle kolumn i wierszy, ile będziesz chciał
- ustawia widżety względem siebie, więc
	- zacznij od widżetu w zerowej kolumnie i zerowym wierszu
	- każdy kolejny ustawiaj względem niego
	- 

```python
from tkinter import Tk, Label, Button, Entry

window = Tk()
window.title("fowfjweoifjwf")
window.minsize(width=500,height=300)

# padding
window.config(padx=100, pady=200)
  

# Label
my_lbl = Label(text="I am a label", font=("Arial", 24, "bold"))
my_lbl.grid(column=0,row=0) # dokleja do okna i centruje

#button 1
btn = Button(text="CLick Me")
btn.grid(column=1, row=1)
btn.config(padx=50, pady=50)
# btn 2
btn2 = Button(text="BTN2", command=lambda: Label(root, text="I am clicked").grid(column=1, row=0))
btn2.grid(column=3,row=0)
# fg="blue" font color blue
# bg = "#ffffff" background color black


# Entry
<<<<<<< HEAD
input = Entry(window, width=10)
=======
input = Entry(width=10)
>>>>>>> remotes/origin/master
input.grid(column=4,row=3)
  

window.mainloop()
```

<<<<<<< HEAD

```python
# Przywitacz
=======
```python
>>>>>>> remotes/origin/master
from tkinter import *

root = Tk()
e = Entry(root, width=50)
e.pack()
# e.insert(0, "Enter your name: ")

def myClick():
	hello = "Hello "+ e.get()
	myLabel = Label(root, text=hello)
	myLabel.pack()

<<<<<<< HEAD
myButton = Button(root, text="Enter your name", command=myClick)
=======
myButton = Button(root, text="ENter your name", command=myClick)
>>>>>>> remotes/origin/master
myButton.pack()

root.mainloop()
```



<<<<<<< HEAD
## TROCHĘ RÓŻNYCH WIDŻETÓW

```python
from tkinter import *

#Creating a new window and configurations
window = Tk()
window.title("Widget Examples")
window.minsize(width=500, height=500)

#Labels
label = Label(text="This is old text")
label.config(text="This is new text")
label.pack()

#Buttons
def action():
    print("Do something")

#calls action() when pressed
button = Button(text="Click Me", command=action)
button.pack()

#Entries
entry = Entry(width=30)
#Add some text to begin with
entry.insert(0, string="Some text to begin with.")
#Gets text in entry
print(entry.get())
entry.pack()

#Text
text = Text(height=5, width=30)
#Puts cursor in textbox.
text.focus()
#Adds some text to begin with.
text.insert(END, "Example of multi-line text entry.")
#Get's current value in textbox at line 1, character 0
print(text.get("1.0", END))
text.pack()

#Spinbox
def spinbox_used():
    #gets the current value in spinbox.
    print(spinbox.get())
spinbox = Spinbox(from_=0, to=10, width=5, command=spinbox_used)
spinbox.pack()

#Scale
#Called with current scale value.
def scale_used(value):
    print(value)
scale = Scale(from_=0, to=100, command=scale_used)
scale.pack()

#Checkbutton
def checkbutton_used():
    #Prints 1 if On button checked, otherwise 0.
    print(checked_state.get())
#variable to hold on to checked state, 0 is off, 1 is on.
checked_state = IntVar()
checkbutton = Checkbutton(text="Is On?", variable=checked_state, command=checkbutton_used)
checked_state.get()
checkbutton.pack()

#Radiobutton
def radio_used():
    print(radio_state.get())
#Variable to hold on to which radio button value is checked.
radio_state = IntVar()
radiobutton1 = Radiobutton(text="Option1", value=1, variable=radio_state, command=radio_used)
radiobutton2 = Radiobutton(text="Option2", value=2, variable=radio_state, command=radio_used)
radiobutton1.pack()
radiobutton2.pack()


#Listbox
def listbox_used(event):
    # Gets current selection from listbox
    print(listbox.get(listbox.curselection()))

listbox = Listbox(height=4)
fruits = ["Apple", "Pear", "Orange", "Banana"]
for item in fruits:
    listbox.insert(fruits.index(item), item)
listbox.bind("<<ListboxSelect>>", listbox_used)
listbox.pack()
window.mainloop()


```
=======


>>>>>>> remotes/origin/master







