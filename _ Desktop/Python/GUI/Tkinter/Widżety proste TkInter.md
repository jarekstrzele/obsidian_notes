```python
from tkinter import *

 

# ogólne
# bg - kolor tła widżetu
# bd - szerokość obramowania widżetu
# font - font tekstu widżetu
# padx, pady wewnętrzna odległość zawartości od granicy


# Creating a new window and configurations
window = Tk()
window.title("Widget Examples")
window.minsize(width=500, height=500)

# Labels
label = Label(text="This is old text")
label.config(text="This is new text")
label.pack()

  

# Buttons
def action():
	print("Do something")
  

# calls action() when pressed
button = Button(text="Click Me", command=action)
button.pack()

# Entry jedno liniowe pole do wprowadzania tekstu
# wielotekstowym jest 'Text' widżet
# Ogólnie e = Entry(master, option, ...) master -partent window
entry = Entry(width=30)
# Add some text to begin with
entry.insert(0, string="Some text ")
# entry.insert(3, "Nowy tekst")
# entry.insert(END, "Nowy tekst")


# Gets text in entry
# zwraca aktualną zawartość widżetu jako string
print(entry.get())
entry.pack()


# Text(master, option, ...) zarządzanie wielowierszowym tekstem
text = Text(height=5, width=30)
# Puts cursor in textbox.
text.focus()
# Adds some text to begin with.
text.insert(END, "Example of multi-line text entry.")
# Get's current value in textbox at line 1, character 0
# get(startindex [,endindex])
print(text.get("1.0", END))
text.pack()
  

# Spinbox jak Entry, ale wybierane są określone wartości libowe
def spinbox_used():
# gets the current value in spinbox.
print(spinbox.get())
# from_ - minimalna liczna , to - maksymalna liczba
spinbox = Spinbox(from_=0, to=10, width=5, command=spinbox_used)
spinbox.pack()
  

# Scale
# Called with current scale value.
def scale_used(value):
	print(value)

scale = Scale(from_=0, to=100, command=scale_used)
scale.pack()
  

# Checkbutton
def checkbutton_used():
# Prints 1 if On button checked, otherwise 0.
	print(checked_state.get())
# variable to hold on to checked state, 0 is off, 1 is on.
checked_state = IntVar()
checkbutton = Checkbutton(
text="Is On?", variable=checked_state, command=checkbutton_used)
checked_state.get()
checkbutton.pack()

  
  

# Radiobutton

def radio_used():
	print(radio_state.get())

# Variable to hold on to which radio button value is checked.
radio_state = IntVar()
radiobutton1 = Radiobutton(text="Option1", value=1,
variable=radio_state, command=radio_used)
radiobutton2 = Radiobutton(text="Option2", value=2,
variable=radio_state, command=radio_used)
radiobutton1.pack()
radiobutton2.pack()

  
  

# Listbox - aby wyświetliś listę elementów, z który użytkownik może wybrać
def listbox_used(event):
# Gets current selection from listbox
	print(listbox.get(listbox.curselection()))

listbox = Listbox(height=4)
fruits = ["Apple", "Pear", "Orange", "Banana"]
for item in fruits:
listbox.insert(fruits.index(item), item) # pierwszy arg to indeks, drugi to element
#<<ListBoxSelect>> to zdarzenie, które zostanie powiązane z funkcją listbox_used
listbox.bind("<<ListboxSelect>>", listbox_used)
listbox.pack()
  
  
  

window.mainloop()
```