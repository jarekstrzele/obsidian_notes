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
input = Entry(width=10)
input.grid(column=4,row=3)
  

window.mainloop()
```

```python
from tkinter import *

root = Tk()
e = Entry(root, width=50)
e.pack()
# e.insert(0, "Enter your name: ")

def myClick():
	hello = "Hello "+ e.get()
	myLabel = Label(root, text=hello)
	myLabel.pack()

myButton = Button(root, text="ENter your name", command=myClick)
myButton.pack()

root.mainloop()
```












