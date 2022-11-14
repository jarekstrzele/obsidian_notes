https://iconarchive.com/
#udemy #gui #python #eramo_michael

---
[[3 Hello GUI World]]





---
# Basics
[[#Button]]
[[#Frame]]
[[#Radio Button]]
[[#Images]]


```python
import tkinter

root = tkinter.Tk()
root.title("Basics")

# https://iconarchive.com/
root.iconbitmap('thinking.ico') #string -> refrence to bitmap
root.geometry('400x400')
root.resizable(0,1) # 1 allow, 0 not allow
root.config(bg='blue')

# second window
top = tkinter.Toplevel()
top.title('Second window')
top.config(bg='#123456')
top.geometry('400x400+500+500') # first +500 x, second+500 y
lbl1 = tkinter.Label(top, text="hello, I am label 1", font=("Cambria", 10), bg="#ff0000", fg='white')
lbl1.pack(padx=10, pady=50)
 

lbl2 = tkinter.Label(top, text="I am the second label", font=("Robot", 12))
lbl2.pack(pady=(0,10), ipadx=50, ipady=10, anchor='w') # 0 - top, 10 - bottom, ipad - internal padding, ancor - west east

lbl3 = tkinter.Label(top, text="I am the third label", font=('Courier', 12), bg='#ffffff', fg='#123456')
lbl3.pack(fill='x')

# lbl3.pack(fill='y', expend=True)
# lbl3.pack(fill='both', expend=True, padx=10,pady=10)

root.mainloop()
```

## Button
```python
import tkinter
 

root=tkinter.Tk()
root.title("Btb")
root.geometry('500x500')
root.resizable(0,0)

btn1 = tkinter.Button(root, text="Name")
btn1.grid(row=0, column=0)
btn2 = tkinter.Button(root, text="Time", bg="#00ffff")
btn2.grid(row=0, column=1)
btn3 = tkinter.Button(root, text="Time", bg="#00ffff", activebackground="#ff0000")
btn3.grid(row=0, column=2, padx=10, pady=10, ipadx=15)

btn4 = tkinter.Button(root, text="Day", bg="black", fg="white", borderwidth=5)
btn4.grid(row=1, column=0, columnspan=3, sticky="WE")

root.mainloop();
```

## Frame
When you use frames you can use layout manager what you want (you cam mix them).
```python
import tkinter
from tkinter import BOTH

root= tkinter.Tk()
root.title("Fame")
root.geometry("500x500")

# def frames
pack_frame = tkinter.Frame(root, bg='red')

grid_frame_2 = tkinter.LabelFrame(root, text="Grid sys rules", borderwidth=5)

pack_frame.pack(fill=BOTH, expand=True)
grid_frame_1.pack(fill='x', expand=True)
grid_frame_2.pack(fill=BOTH, expand=True, padx=10, pady=10)

# frame pack
tkinter.Label(pack_frame, text='text').pack()
tkinter.Label(pack_frame, text='text').pack()
tkinter.Label(pack_frame, text='text').pack()

# frame
# grid
tkinter.Label(grid_frame_1, text='text').grid(column=0, row=0)
tkinter.Label(grid_frame_1, text='text').grid(column=1, row=1)
tkinter.Label(grid_frame_1, text='text').grid(column=2, row=2)

tkinter.Label(grid_frame_2, text='tfweweweweweweweweweweweweweext').grid(column=0, row=0)

root.mainloop()
```

```python
import tkinter
from tkinter import END

root = tkinter.Tk()
root.title('Some Basics')
root.geometry("500x500")
def make_label():
	text = tkinter.Label(output_frame, text=text_entry.get(), bg='#ff0000')
text.pack()
text_entry.delete(0, END);

input_frame = tkinter.Frame(root, bg="#0000ff", width=500, height=100)
output_frame = tkinter.Frame(root, bg="#ff0000", width=500, height=400)

input_frame.pack(padx=10, pady=(10,5)) #(top, bottom)
output_frame.pack(padx=10, pady=(0, 10))

text_entry = tkinter.Entry(input_frame, width=40)
text_entry.grid(row=0, column=0, padx=5, pady=5)
input_frame.grid_propagate(0) # 0 -the frame no longer resize to the zise of the widgets that it contains
print_button = tkinter.Button(input_frame, text="Print!", command=make_label)
print_button.grid(row=0, column=1, padx=5, pady=5, ipadx=30)

# keep output frame size
output_frame.pack_propagate(0)

root.mainloop()
```


## Radio Button
```python
import tkinter
from tkinter import IntVar # StringVar
  

root = tkinter.Tk()
root.title('Some Basics')
root.geometry("500x500")

def make_label():
	if number.get() == 1:
		num_label=tkinter.Label(out_frame, text='1 one 1')
	elif number.get() == 2:
		num_label=tkinter.Label(out_frame, text="2 two 2")
	num_label.pack()


in_frame = tkinter.LabelFrame(root, text="this is fun!", width=350, height=100)
out_frame = tkinter.Frame(root, width=350, height=250)
in_frame.pack(padx=10, pady=10)
out_frame.pack(padx=10, pady=(0,10))

number = IntVar()
number.set(1)
radio1=tkinter.Radiobutton(in_frame, text="print hte number one!", variable=number, value=1)
radio2=tkinter.Radiobutton(in_frame, text="Print the number two!", variable=number, value=2)
print_button = tkinter.Button(in_frame, text="Print the number!", command=make_label)
  

radio1.grid(row=0,column=0, padx=10, pady=10)
radio2.grid(row=0,column=1, padx=10, pady=10)
print_button.grid(row=1,column=0, columnspan=2, padx=10, pady=10)

root.mainloop()
```

## Images
```python
import tkinter
from PIL import ImageTk, Image # to work with jpg
# pip install pillow

root = tkinter.Tk()
root.geometry("500x500")

def make_cat_image():
	global cat_image
	cat_image = ImageTk.PhotoImage(Image.open('cat.jpeg'))
	cat_lbl = tkinter.Label(root, image=cat_image)
	cat_lbl.pack()

# png file
# 1. create the image
# 2. put the image onto a label or a button or some other widget
# 3. Put that widget onto the screen
# PNG this is not work with JPEG

my_image = tkinter.PhotoImage(file='male_face.png') # first step
my_lbl = tkinter.Label(root, image=my_image) # second step
my_lbl.pack()

my_btn = tkinter.Button(root, image=my_image)
my_btn.pack()

# JPG - using PIL
# my_image2 = tkinter.PhotoImage(file='cat.jpeg') # first step
# my_lbl2 = tkinter.Label(root, image=my_image) # second step
# my_lbl2.pack()

# this code works well
# cat_image = ImageTk.PhotoImage(Image.open('cat.jpeg'))
# cat_lbl = tkinter.Label(root, image=cat_image)
# cat_lbl.pack()

# when you want to display an image with a function
# you have to use global variable
# otherwise Garbage Collactor clean the variable
make_cat_image()

root.mainloop()
```







