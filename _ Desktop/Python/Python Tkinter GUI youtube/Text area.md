#gui #python #tkinter  #textarea


```python
from tkinter import *

def submit():
    input = text.get("1.1", END) #"row.column"
    print(input)

root=Tk()
root.geometry("600x450")

# wielkość obiekty Text zależy od wielkości czcionki
# aby to opanować należy ustaliź width, height (ilośc liter)

text = Text(root, bg="light yellow", font=("Arial", 25),
             width=30, height=10, padx=10, pady=10, fg="red")
text.pack()

btn=Button(root, text="Submit", command=submit,  padx=10, pady=10 )
btn.pack(ipadx=10, ipady=10)

root.mainloop()
```








