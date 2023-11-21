#python #tkinter  #udemy  #yu_angela 

https://www.udemy.com/course/100-days-of-code/learn/lecture/20781124#overview


```python
import tkinter

window = tkinter.Tk()
window.title("My first gui program")
window.minsize(width=500,height=300)

my_lbl = tkinter.Label(text="I am a label", font=("Arial", 24, "bold"))
my_lbl.pack(side="left", expand=True)
  

window.mainloop()
```


```python
from tkinter import *

window = Tk()
window.title("My first gui program")
window.minsize(width=500,height=300)

my_lbl = Label(text="I am a label", font=("Arial", 24, "bold"))
my_lbl.pack(side="left", expand=True)
my_lbl["text"]="New Text"
my_lbl.config(text="The second new text")

def btn_click():
    print("I got clicked")
    #print(entry.get())
    #my_lbl.config(text="Button got clicked")
    my_lbl.config(text=entry.get())
  

btn = Button(text="click me", command=btn_click)
btn.pack()

entry = Entry(width=10)
entry.pack()
  

window.mainloop()
```








