

# Tkinter
Popularny *GUI toolkit*.
Elementy GUI będą tworzone przez konkretyzację obiektów klasy z moduły `tkinter`.

Programy obsugujące GUI są sterowane zdarzeniami (*event-driven*). Kolejność wykonywanych działań nie zależy od kolejności napisanego kodu, ale od aktywności użytkowanika.

W programie typu *event-driven* ZDARZENIA  (*events*) są powiązane z PROCEDURAMI OBSŁUGI ZDARZEŃ (*event handler* - to kod, który jest wykonywany, gdy wystąpiło okreśone zdarzenie).

Definiując wszystkie obiekty, zdarzenia, procedury obsługi zdarzeń, programista ustala sposób działania programu.
**Pętla obsługi zdarzeń** powoduje, że program nieustannie oczekuje wystąpienia danego zdarzenia.

samotne okno
```python
from tkinter import *

# utworzenie obiektu klasy Tk()
root = Tk() #tworzenie okna głównego
root.title("Proste GUI")
root.geometry("225x100")

# pętla zdarzeń
root.mainloop()
```

Elementy GUI to widżety (*widgets = window gadgets*).

## Ramka *Frame*
==frame== 
- przechowuje inne widżety; 
- jest jak korkowe tworzywo tablicy ogłoszeń
- tworzona jest przez `Frame(obiekt_nadrzędny)`

>Za każdym razem, gdy tworzysz nowy widżet musisz przekazać do jego konstruktora obiekt nadrzędny (*master*), który będzie zawierał ten widżet

`app = Frame(root)` - utwórz obiekt Frame i umieść go w oknie głównym
`app.grid()` uruchom metodę `grid` obiektu `app` (metoda powiązana z menadźerem układów *layout manager*)
`lbl = Label(app, text="To ja, twoja etykietka")`  utwórz obiekt `Label` (to nieedytowalny tekst lub ikona; etykieta nie jest interaktywna)
`app` (czyli obiekt/ramka klasy `Frame`) jest obiektem nadrzędnym dla `lbl`

```python
from tkinter import *

# utworzenie obiektu klasy Tk()
root = Tk()
root.title("Proste GUI")
root.geometry("225x100")

app = Frame(root)
app.grid()

lbl = Label(app, text="To ja, twoja etykietka")
lbl.grid()

# pętla zdarzeń
root.mainloop()
```

## Button
```python
from tkinter import *
# utworzenie obiektu klasy Tk()
root = Tk()
root.title("Proste GUI")
root.geometry("225x100")

app = Frame(root)
app.grid()

btn1 = Button(app, text="Jestem btn1") #obiektem nadrzędnym dla btn1 jest app
btn1.grid()

btn2 = Button(app)
btn2.grid()
btn2.configure(text="Ja za to jestem btn2 ZZzzz")

btn3 = Button(app)
btn3.grid()
btn3["text"] = "To ja btn3 z []"

lbl = Label(app, text="To ja, twoja etykietka")
lbl.grid()

# pętla zdarzeń
root.mainloop()
```

----
## GUI z klasą
>	`super()` 
>	- metoda, która umożliwia dostęp do metod i atrybutów klasy rodzica 
>	- zwraca obiekt będący reprezentacją klasy rodzica


```python
from tkinter import *

class App(Frame):
	def __init__(self, master):
		super(App, self).__init__(master)
		self.grid()
		self.create_widgets()

	def create_widgets(self):
		self.btn1 = Button(self, text="Pierwszy")
		self.btn1.grid()
		self.btn2 = Button(self)
		self.btn2.grid()
		self.btn2.configure(text="Drugi")
		self.btn3 = Button(self)
		self.btn3.grid()
		self.btn3["text"] = "No i trzeci"

root =Tk()
root.title("Przyciski z klasą")
root.geometry("210x85")

app = App(root)
app.grid()

root.mainloop()
```

-----

##  Obsługa zdarzeń przez Widgety


`Button(<container>, text, command)`
`<container>` komponent rodzic, do którego przycisk zostanie "przyczepiony"
`text` napis umieszczony na przycisku
`command` nazwa funkcji *callback*, czyli takie, która zostanie uruchomiona, gdy wystąpi zdarzenie naciśnięcia przycisku
```python
from tkinter import *

class App(Frame):
	def __init__(self, master):
		super(App, self).__init__(master) # równoważne super().
		self.grid()
		self.bttn_clicks = 0
		self.create_widgets()

	def create_widgets(self):
		self.btn1 = Button(self, text="Liczba kliknięć: 0")
		self.btn1["command"] = self.update_count_plus # powiązanie kliknięcia z obsługą tego zdarzenia
		self.btn1.grid()

		self.btn2 = Button(self, text="Liczba kliknięć: 0")
		self.btn2["command"] = self.update_count_minus # powiązanie kliknięcia z obsługą tego zdarzenia
		self.btn2.grid()

	def update_count_plus(self):
		self.bttn_clicks += 1
		self.btn1["text"] = "Liczba kliknięć: " + str(self.bttn_clicks)
	
	def update_count_minus(self):
		self.bttn_clicks -= 1
		self.btn1["text"] = "Liczba kliknięć: " + str(self.bttn_clicks)

  

root = Tk()
root.title("Przyciski z klasą")
root.geometry("210x85")
 

app=App(root)
app.grid()

root.mainloop()
```

----------

## widżety `Text`, `Entry`
`Entry` jednowierszowy
`Text` wielowierszowy

```python
from tkinter import *

class App(Frame):
	def __init__(self, master):
		super(App, self).__init__(master) # równoważne super().
		self.grid()
		self.create_widgets()

	def create_widgets(self):
		self.inst_lbl = Label(self, text="Wprowadź hasło")
		# row, column koordynaty w obrębie widżetu nadrzędnego
		# columnspan - rozciągnięcie widżetu na więcej niż jedną kolumnę
		# sticky, jego wartości to kierunki świat N S E W
		# sticky=W - wyrównaj etykietę do lewej strony
		self.inst_lbl.grid(row=0, column = 0, columnspan =2, sticky=E)
		self.pw_lbl = Label(self, text="Hasło: ")
		self.pw_lbl.grid(row=1, column=0, sticky=E)

		self.pw_ent=Entry(self)
		self.pw_ent.grid(row=1, column=1, sticky=W)

		self.submit_bttn=Button(self, text="Akceptuj", command=self.reveal)
		self.submit_bttn.grid(row=2, column=0, sticky=W)

		# wrap ma wartości WORD, CHAR, NONE
		# wrap <- jak zwijać tekst
		self.secret_msg = Text(self, width=35, height=5, wrap=WORD)

		self.secret_msg.grid(row=3, column=0, columnspan=2, sticky=W)

	def reveal(self):
		# get() - zwraca tekst zawarty w widżecie
		# get występuje u Entry oraz u Text
		contents = self.pw_ent.get()

		if contents == "topsecret":
			msg = "Oto tajemnica tajemnic : 54"
		else:
			msg = "Hasło niepoprawne!! SPadaj!"

		# delete - usuwa stringa z widżetu Text
		# 0.0 => wiersz.kolumna; delete usunie wszystko od pozycji wiersz=0, kolumna=0
		self.secret_msg.delete(0.0, END)
		# insert - wstawia string do widźetu tekstowego
		# 0.0 jak wyżej, czyli od wiersz.kolumna
		# insert - nie zastępuje istniejącego tekst
		self.secret_msg.insert(0.0, msg)


# --------
root = Tk()
root.title("Entry i Text")
root.geometry("210x85")

app=App(root)
app.grid()

root.mainloop()
```


---
## Checkbutton
```python
from tkinter import *

class App(Frame):
	"""App pozwalająca wybrać ulubione dania"""
	def __init__(self, master):
		super(App, self).__init__(master)
		self.grid()
		self.create_widgets()

	def create_widgets(self):
		# dostęp do tej etykiety nie jest potrzebny
		# etykieta-obiekt jest atrybutem biektu App(Frame)
		Label(self, text="Wybierz swoje ulubione mięso").grid(row=0,column=0,sticky=W)
		Label(self, text = "Zaznacz dania, które lubisz").grid(row=1, column=0, sticky=W)

	# pola wyboru, potrzebują specjalnego obiektu, który
	# będzie odzwierciedlał stan pola wyboru -> obiekt klasy BooleanVar z modułu tkinter
	
	# wołowina
	self.likes_beef = BooleanVar()
	Checkbutton(self,
		text="wołowina",
		variable = self.likes_beef,
		command = self.update_text
		).grid(row=2,column=0,sticky=W)

	# drób
	self.likes_poultry=BooleanVar()
	Checkbutton(self,
		text="drób",
		variable=self.likes_poultry,
		command=self.update_text
	).grid(row=3,column=0,sticky=W)\

	# ryba
	self.likes_fish=BooleanVar()
	Checkbutton(self,
		text="ryba",
		variable=self.likes_fish,
		command=self.update_text
	).grid(row=4,column=0,sticky=W)


# pole tekstowe do wyświetlenia wyników
	self.results_txt = Text(self, width=40, height=5, wrap=WORD)
	self.results_txt.grid(row=5, column=0, columnspan=3)
  

	def update_text(self):
	"""Aktualizacja pola tekstowego i
	wyświetlanie mięs wybranych przez użytkownika"""
  

		likes=""
		if self.likes_beef.get():
			likes += "Lubisz wołowinę, świetnie\n"
		if self.likes_poultry.get():
			likes += "Lubisz drób, kokoko spoko\n"
		if self.likes_fish.get():
			likes += "Lubisz wkąszać rybkę\n"

		self.results_txt.delete(0.0, END)
		self.results_txt.insert(0.0, likes)


def main():
	root = Tk()
	root.title("Manager mięs")
	app = App(root)
	root.mainloop()

main()
```































