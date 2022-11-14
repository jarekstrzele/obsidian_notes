#tkinter 


# Calculator
```python
from struct import calcsize
from tkinter import *

root = Tk()
root.title("Simple calc")

e = Entry(root, width=35, borderwidth=5)
e.grid(row=0, column=0, columnspan=3, padx=10, pady=10)

def click(num):
# curr = e.get()
# e.delete(0, END)
# e.insert(0, str(curr) + str(num))
	e.insert(END, str(num))

def add():
	first_num = e.get()
	global f_num
	global calc
	calc = "add"
	f_num = int(first_num)
	e.delete(0, END)
  

def substraction():
	first_num = e.get()
	global f_num
	global calc
	calc = "substract"
	f_num = int(first_num)
	e.delete(0, END)

def equal():
	second_num = e.get()
	e.delete(0, END)
	if calc == "add":
		e.insert(0, f_num + int(second_num))
	if calc == "substract":
		e.insert(0, f_num - int(second_num))
  

btn1 = Button(root, text="1", padx=40, pady=20, command=lambda: click(1))
btn2 = Button(root, text="2", padx=40, pady=20, command=lambda: click(2))
btn3 = Button(root, text="3", padx=40, pady=20, command=lambda: click(3))
btn4 = Button(root, text="4", padx=40, pady=20, command=lambda: click(4))
btn5 = Button(root, text="5", padx=40, pady=20, command=lambda: click(5))
btn6 = Button(root, text="6", padx=40, pady=20, command=lambda: click(6))
btn7 = Button(root, text="7", padx=40, pady=20, command=lambda: click(7))
btn8 = Button(root, text="8", padx=40, pady=20, command=lambda: click(8))
btn9 = Button(root, text="9", padx=40, pady=20, command=lambda: click(9))
btn0 = Button(root, text="0", padx=40, pady=20, command=lambda: click(0))
btn_to_add = Button(root, text="+", padx=39, pady=20, command=add)
btn_to_subtract = Button(root, text="-", padx=39,
pady=20, command=substraction)
btn_equal = Button(root, text="=", padx=91, pady=20, command=equal)
btn_clear = Button(root, text="clear", padx=79, pady=20,
command=lambda: e.delete(0, END))

btn1.grid(row=3, column=0)
btn2.grid(row=3, column=1)
btn3.grid(row=3, column=2)

btn4.grid(row=2, column=0)
btn5.grid(row=2, column=1)
btn6.grid(row=2, column=2)

btn7.grid(row=1, column=0)
btn8.grid(row=1, column=1)
btn9.grid(row=1, column=2)

btn0.grid(row=4, column=0)
btn_to_add.grid(row=5, column=0)
btn_to_subtract.grid(row=6, column=0)
btn_equal.grid(row=5, column=1, columnspan=2)
btn_clear.grid(row=4, column=1, columnspan=2)

root.mainloop()
```
