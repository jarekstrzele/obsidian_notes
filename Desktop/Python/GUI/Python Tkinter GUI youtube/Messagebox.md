#python #gui #messagebox

```python

from tkinter import *
from tkinter import messagebox

win=Tk()

def click():
#    messagebox.showinfo(title="zwykłe info", message="Jesteś super!")
#    messagebox.showwarning(title="Ostnie ostrzeżenie", message="Zacznij się uczyć!")
#    messagebox.showerror(title="Błąd mózgu", message="Twój mózg się przegrzał")
    # if messagebox.askokcancel(title="Wybór tabletki", message="Czy wybierasz niebieską tabletkę?"):
    #     print("Pozostajesz w Matrixe")
    # else:
    #     print("Wyszedłeś  z Matrixa")

    #similar messagebox.askretrycancel

    # podobnie messagebox.askyesno(title="Jedzenie robaków", message="Lubisz jeść robaki?")

     #print(messagebox.askquestion(title='ask question', message='Do you like pie?')) # -> return 'yes' or 'no'

    answer = messagebox.askyesnocancel(title='yes, no, cancel', message='Do you like to watch a movie')
    # you can change icon
    # messagebox.askyesnocancel(title='yes, no, cancel', message='Do you like to watch a movie', icon='warring') # 'error'

    print(answer)

btn = Button(win, command=click, text="kliknij mnie")
btn.pack()
win.mainloop()

```