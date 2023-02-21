[[_ basics GUI Python]]

https://coolors.co/


```python
import tkinter
from tkinter import BOTH, StringVar, END
from PIL import ImageTk ,Image

root = tkinter.Tk()
root.title("Hello GUI world")
# try:
# root.iconbitmap('dog.ico')
# except:
# print("error")
root.geometry("400x400")
root.resizable(0,0)
  

# define colors, fonts
root_color = "#224870"
input_color="#2a4494"
output_color="#4ea5d9"
root.config(bg=root_color)

# define function
def submit_name():
# Create a label for the user name based of radio button values
	if case_style.get() == 'normal':
		name_label = tkinter.Label(output_frame, text="Hello " + name.get() + "! Keep going!", bg=output_color)
	elif case_style.get() == 'upper':
		name_label = tkinter.Label(output_frame, text=("Hello " + name.get() + "! Keep going!").upper(), bg=output_color)

	name_label.pack()
	name.delete(0,END)

  
  

# def layout
input_frame = tkinter.LabelFrame(root, bg=input_color)
output_frame = tkinter.LabelFrame(root, bg=output_color)
input_frame.pack(pady=10)
output_frame.pack(padx=10, pady=(0,10), fill=BOTH, expand=True)
  

# create widgets
name = tkinter.Entry(input_frame, text="Enter your name", width=20)
submit_button = tkinter.Button(input_frame, text="Submit", command=submit_name)
name.grid(row=0, column=0, padx=10, pady=10)
submit_button.grid(row=0,column=1, padx=10, pady=10, ipadx=20)
 
# Create radio button for text display
case_style = StringVar()
case_style.set('normal')
normal_button = tkinter.Radiobutton(input_frame, text="Normal Case", variable=case_style,
value='normal', bg=input_color, fg='#EAF7CF')
upper_button = tkinter.Radiobutton(input_frame, text="UPPER Case",
variable=case_style, value='upper', bg=input_color, fg='#EAF7CF')
normal_button.grid(row=1, column=0, padx=2, pady=2)
upper_button.grid(row=1, column=1, padx=2, pady=2)

# add an image
rabbit_img = ImageTk.PhotoImage(Image.open('alc-icon.png'))
rabbit_lbl = tkinter.Label(output_frame, bg=output_color, image=rabbit_img)
rabbit_lbl.pack()

root.mainloop()
```



