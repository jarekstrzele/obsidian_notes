OBIEKTOWO
First:
```python
import tkinter
from tkinter import StringVar, IntVar, scrolledtext

class App(tkinter.Tk):
    menu_color = "#bdb9db"
    root_color = "#6c809a"
    def __init__(self, title="Notepad", icon="images/pad.ico", size="600x600", shape=(0,0)):
        super().__init__()
        self.title(title)
        self.iconbitmap(icon)
        self.geometry(size)
        self.resizable(*shape)
        self.config(bg=App.root_color)

    def run(self):
        self.mainloop()

    def create_wigets(self):
        self.menu = Menu(self)
        self.menu.pack(padx=5, pady=5)
        self.menu.close.config(command=self.test)
        self.notes=Notes(self)

        # self.notes.config(font=self.menu.fonts_types.chosen_font.get())
        self.notes.config(font=self.menu.fonts_types.get())
        self.notes.pack()

    def test(self):
        print("destrou")

class Menu(tkinter.Frame):
    def __init__(self, master, bg="#bdb9db"):
        super().__init__(master)
        # self.new_img = tkinter.PhotoImage(file='images/new.png')
        # self.new_btn = tkinter.Button(self, image=self.new_img)
        # self.new_btn.grid(row=0, column=0, padx=5, pady=5)
        # self.open_img = tkinter.PhotoImage(file='images/open.png')
        # self.open_btn = tkinter.Button(self, image=self.open_img)
        # self.open_btn.grid(row=0, column=1, padx=5, pady=5)
        # self.save_img = tkinter.PhotoImage(file='images/save.png')
        # self.save_btn = tkinter.Button(self, image=self.save_img)
        # self.save_btn.grid(row=0, column=2, padx=5, pady=5)
        # self.close_img = tkinter.PhotoImage(file='images/close.png')
        # self.close_btn = tkinter.Button(self, image=self.close_img)
        # self.close_btn.grid(row=0, column=3, padx=5, pady=5)
        self.new=MenuWidgets(self, 'images/new.png')
        self.open=MenuWidgets(self, 'images/open.png', column=1)
        self.save=MenuWidgets(self, 'images/save.png', column=2)
        self.close=MenuWidgets(self, 'images/close.png', column=3)
        self.close.btn.config(command=quit)
        self.fonts_types=TypeFontChooser(self, column=4)
        self.sizes_types=SizeFontChooser(self, column=5)
        self.format_types=FormatFontChooser(self, column=6)
  

class MenuWidgets(tkinter.Button):
    def __init__(self, master, image_path, row=0, column=0, padx=5, pady=5):
        super().__init__(master)
        self.img=tkinter.PhotoImage(file=image_path)
        self.btn=tkinter.Button(master, image=self.img)
        self.btn.grid(row=row,column=column, padx=padx, pady=pady)  

class TypeFontChooser(tkinter.OptionMenu):
    families=['Terminal', 'Modern', 'Lato', 'Roboto', 'Noto', 'Alef', 'Carlito', 'Arial', 'Calibri', 'Impact']
    def __init__(self, master, row=0, column=0, padx=5, pady=5):
        self.chosen_font=StringVar()
        self.chosen_font.set('Terminal')
        self.set = self.chosen_font.set
        self.get = self.chosen_font.get
        super().__init__(master, self.chosen_font, *TypeFontChooser.families)
        self.config(width=16)
        self.grid(row=row, column=column, padx=padx, pady=pady)

    def change_font(self, event):
        def func(event):
            print('hello')

        self.config(command=func)
  

class SizeFontChooser(tkinter.OptionMenu):
    size=[8,10,12,14,16,20,24,32,48,64,72,96]
    def __init__(self, master, row=0, column=0, padx=5, pady=5):
        self.chosen_size=IntVar()
        self.chosen_size.set(12)
        super().__init__(master, self.chosen_size, *SizeFontChooser.size)
        self.config(width=2)
        self.grid(row=row, column=column, padx=padx, pady=pady)

  

class FormatFontChooser(tkinter.OptionMenu):
    formats=['none', 'bold', 'italic']
    def __init__(self, master, row=0,column=0, padx=5, pady=5):
        self.chosen_format=StringVar()
        self.chosen_format.set('none')
        super().__init__(master, self.chosen_format, *FormatFontChooser.formats)
        self.config(width=5)
        self.grid(row=row, column=column, padx=padx, pady=pady)
  

class Notes(tkinter.scrolledtext.ScrolledText):
    text_color = "#fffacd"
    def __init__(self, master):
        super().__init__(master, bg=Notes.text_color, width=400, height=200)

  

  
  

if __name__ == "__main__":
    app = App()
    app.create_wigets()
    app.run()
```


----------
First step
```python
import tkinter

class App(tkinter.Tk):
    text_color = "#fffacd"
    menu_color = "#bdb9db"
    root_color = "#6c809a"

    def __init__(self, title="Notepad", icon="images/pad.ico", size="600x600", shape=(0,0)):
        super().__init__()
        self.title(title)
        self.iconbitmap(icon)
        self.geometry(size)
        self.resizable(*shape)
        self.config(bg=App.root_color)

    def run(self):
        self.mainloop()

    def create_wigets(self):
        self.menu = Menu(self)
        self.menu.pack(padx=5, pady=5)
        self.menu.close.config(command=self.test)

    def test(self):
        print("destrou")
  

class Menu(tkinter.Frame):
    def __init__(self, master, bg="#bdb9db"):
        super().__init__(master)
        # self.new_img = tkinter.PhotoImage(file='images/new.png')
        # self.new_btn = tkinter.Button(self, image=self.new_img)
        # self.new_btn.grid(row=0, column=0, padx=5, pady=5)

        # self.open_img = tkinter.PhotoImage(file='images/open.png')
        # self.open_btn = tkinter.Button(self, image=self.open_img)
        # self.open_btn.grid(row=0, column=1, padx=5, pady=5)
        # self.save_img = tkinter.PhotoImage(file='images/save.png')
        # self.save_btn = tkinter.Button(self, image=self.save_img)
        # self.save_btn.grid(row=0, column=2, padx=5, pady=5)
        # self.close_img = tkinter.PhotoImage(file='images/close.png')
        # self.close_btn = tkinter.Button(self, image=self.close_img)
        # self.close_btn.grid(row=0, column=3, padx=5, pady=5)

        self.new=MenuWidgets(self, 'images/new.png')
        self.open=MenuWidgets(self, 'images/open.png', column=1)
        self.save=MenuWidgets(self, 'images/save.png', column=2)
        self.close=MenuWidgets(self, 'images/close.png', column=3)
        self.close.btn.config(command=quit)

  

class MenuWidgets(tkinter.Button):
    def __init__(self, master, image_path, row=0, column=0, padx=5, pady=5):
        super().__init__(master)
        self.img=tkinter.PhotoImage(file=image_path)
        self.btn=tkinter.Button(master, image=self.img)
        self.btn.grid(row=row,column=column, padx=padx, pady=pady)  


if __name__ == "__main__":

    app = App()

    app.create_wigets()

    app.run()
```


# Fonts in tkinter
```python
import tkinter
from tkinter import font

root=Tk()
fonts = font.families()
for font in fonts:
	print(font)
```






