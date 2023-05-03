#youtube  #python #gui  #tkinter 

https://www.youtube.com/watch?v=TuLxsvK4svQ

[[#CheckButton]]
[[#RadioButton]]
[[#Scale]]

[[Listbox]]    [[Colorchooser]]    [[Messagebox]]    [[Text area]]    [[File handler]]
[[Python Menu Bar]]     [[tabs.py]]    [[Progress bar]]   [[Canvas]]  
[[Key event]]    [[Mouse_events]]     [[Drag and Drop]]   
[[move images]]       [[More animations]] 
[[Multi animations]]


---------

## CheckButton
```python
from tkinter import *

win = Tk()

x = IntVar() # StringVar, BoolVar
python_photo = PhotoImage(file='Python-icon.png')

def display():
    if(x.get() == 1):
        print("You love Python")
    else:
        print('You don\'t know tha you love Python')

check_button = Checkbutton(win, text = "I love Python",
                            variable = x,
                            onvalue=1, # Bool : True; String: "Yes"
                            offvalue=0,
                            command=display,
                            font=('Arial', 20 ),
                            fg = '#D7CEF1',
                            bg='#1E6A20',
                            activeforeground='#D7CEF1',
                            activebackground='#1E6A20',
                            padx=25,
                            pady=10,
                            image=python_photo,
                            compound='left')
check_button.pack()

win.mainloop()
```

## RadioButton

```python
from tkinter import *
win=Tk()

superheros = ['Superman', 'Spiderman', 'Batman']

x=IntVar()

superman_img = PhotoImage(file='Superman-icon.png')
spiderman_img = PhotoImage(file='Spiderman-icon.png')
batman_img = PhotoImage(file='Batman-icon.png')

superheros_imgs = [superman_img, spiderman_img, batman_img]


def choose_superhero():  
    if (x.get() == 0):
        print("You choose superman")
    elif (x.get() == 1):
        print("You choose spiderman")
    else:
        print("You choose Batman")

for index in range(len(superheros)):
    radio_btn = Radiobutton(win, text=superheros[index],
        variable=x, # groups radiobtns together id they share the same variable
        value=index, # assigns each radiobtns a different value
        padx = 25,
        font=('Impact', 50),
        image=superheros_imgs[index],
        compound='left',
        indicatoron=0, # eliminate circle indicators
        width =375,
        command = choose_superhero
        )

    radio_btn.pack(anchor=W)      

win.mainloop()
```


## Scale
```pascal
from tkinter import *

win = Tk()
lbl_faren = Label(win, text="Fahrenheit: ...", font=("Arial", 11), padx=20, pady=20)
sun_img = PhotoImage(file='Sun-icon.png')
sun_lbl = Label(image=sun_img)
sun_lbl.pack()
snowman_img = PhotoImage(file='Snowman-icon.png')
snowman_lbl = Label(image=snowman_img)

def submit():
    # print(f'Temperatura: {scale.get()} stopni Celcjusza')
    faren = 9/5 * int(scale.get()) + 32
    lbl_faren.config(text=f"Fahrenheit: {faren}")

scale = Scale(win, from_=100, to=0,
                length=500,
                orient=VERTICAL,
                font=('Consolas', 15),
                tickinterval = 10, # adds numeric indiators for value
                showvalue=0, # hide current value
                troughcolor='#69EAFF',
                fg='red',
                bg='#111111'
                )

scale.pack()
scale.set(50)
# scale.set(((scale['from']-scale['to])/2)+scale['to'])

snowman_lbl.pack()

btn = Button(win, text='submit', command=submit)
btn.pack(padx=20, pady=20)
lbl_faren.pack()

win.mainloop()
```

## ListBox
[[Listbox]]










