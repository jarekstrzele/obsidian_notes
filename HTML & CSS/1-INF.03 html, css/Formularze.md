[[język HTML 5]]

[[Podstawowa struktura pliku HTML 5]]

# Formularze
#html/form
Lista zagadnień:
[[#Znacznik formularza]]
[[#Pole INPUT]]
[[#Pole BUTTON]]
[[#Grupowanie]]
[[#Pole SELECT]]
[[#TEXTAREA]]
[[#Nieaktywne pola formularza]]
[[#DATALIST]]
[[#ATRYBUTY]]
[[#ACTION i METHOD]]


---

Mogą zawierać:
- pola tekstowe, 
- przyciski opcji,
- pola wyboru,
- listy rozwijane
- ...

[[schemat_form_server_DB.excalidraw]]

---

## Znacznik formularza
`<form>   </form>`

### atrybuty
- `action="adres"` 
	- adres (skrypt), na który będzie wysłany formularz,
	- `?subject=temat` parametr umożliwiający wysłanie e-maila `<form action="xxx@gmail.com?subject=temat">`
- `method="post"` określa spośób przekazania iformacji (domyślnie `get`, zaleca się `post`)
---

## Pole `INPUT`
### znacznik
`<input>`

```html
<form action="" method="post">
<p> Podaj swoje imię: </p>
<input type="text" name="imie" value="">
<input type="submit" value="Wyślij">
</form>
```

### atrybuty
- `name` określa nazwę danego pola oraz nazwę zmiennej, do której zostanie podstawiona wprowadzona wartość
- `value` domyślna wartość pola
- `size` liczba znaków w widocznej części pola
- `maxlength` malsymalna liba znaków, jaką można wpisać
- `type` typ pola:
	- `type="text"` tekst jednowierszowy; wartość domyślna
	- `type="checkbox"` pole zaznaczenia opcji
		```html<p><input type="checkbox" name="opcja"> Zgadzam się na przetwarzanie moich danych osobowych <p>`
	- `type="radio"` pole wyboru jednej opcji
```html
	<h3>Wykształceie<h3>
<!-- komentarz  
-->

	<p>
	<input  type="radio" value="Podstawowe" name="grupa_opcji" checked> Podstawowe<br/>
      <input type="radio" value="Średnie" name="grupa_opcji"> Średnie<br>
      <input type="radio" value="Wyższe" name="grupa_opcji"> Wyższe</p>


```
`checked` pole domyślnie wybrane
atrybut `name` musi mieć we wszystkich ploch taką samą nazwę
atrybut `value` musi mieć określoną wartość i różna dla każdego pola

- `type="password"`
`<p>Podaj hasło: <input type="password" name="haslo" size="10 maxlength="14"></p>`
- `type="file"` doączanie do formularza pliku
- `type="submit"` przycisk, który uruchamia akcję zdefiniowaną w atrybucie `action`
-  `type="reset"` usuwa zawartości wszystkich pól
-  `type="hidden"` pole tekstowe nie widoczne na stronie; jego zawartość jest przesyłana wraz z formularzem (np. zwiera informację z formularzy wcześnie wypełnionych przez użytkowanika)
- `type="email"
-  `type="button"` przycisk dowolnego przeznaczenia, jego działanie definiowane przez skrypt
- `type=color` ustawianie koloru
```html
<form action="" method="post">
<p>Wybierz kolor"" </p>
<input type="color" name="kolor" value="#ff0000">
<input type="submit" value="Wyślij">

</form>

```

- `type=number` wprowadzanie liczb całkowitych
```html
<input type="number" name="liczba" min="10" max="99" step="10" value="20">
<input type="submit" value="Wyślij">
```
- `type="date"` wprowadzanie daty
```html
<input type="date" name="data" >
<input type="submit" value="Wyślij">
```

---
## Pole `BUTTON`
Podobne do pola `input` (różnica: można zmieniać wygląd `button`, ma atrybut `style`)

### znacznik
`<button> Tekst </button>`

Jego atrybut type przyjmuje wartości:
- `submit`
- `reset`
- `button`

`<button type="submit" name="przycisk" style="font: 12pt Arial; background: red">Przycisk</button>`

### Etykieta
Aby związać tekst etykiety opisującej pole używamy
`<label> Treść </label>`

```html
<label>
	<input type="checkbox" name="nazwa" value="wartość"> Etykieta pola
</label>
<br>

<label for="pole"> Etykieta pola z id </label>
<input id="pole" type="checkbox" name="nazwa" value="wartość" >


```

```html
<h3> Wykształcenie </h3>
<label> 
	<input type="radio" value="Podstawowe" name="wybor" checked> Podstawowe </label>
<br>

<label>
<input type="radio" value="Średnie" name="wybor"> Średnie </label>
<br>

<label>
<input type="radio" value="Wyższe" name="wybor" checked> Wyższe</label>
<br>
```

---

## Grupowanie
```html
<fieldset>
<legend>Tytuł</legend>
Elementy grupy
</fieldset>

```


---


## Pole `SELECT`
Wyświetlanie w formularzu listy wartości do wyboru.

### znacznik
`<select> </select>` definiuje listę
`<option> </option>` definiuje elementy listy
```html
<select name="moja_lista">
<option> First </option>
<option> Second </option>
<option> Third </option>
</select>

```

### atrybuty
dla `select`:
- `size="n"` _n_ liczba pozycji widocznych w polu `SELECT`

dla `<option>`:
- `selected` definiuje element domyślnie wybrany (default the first element)
- `value="wartość"` określa wartość danej pozycji przekazywaną przez wysyłany formularz

```html
<h3> Formularz zamówienia <h3>
  <select name="napoj" size="5" multiple>
    <option> kawa czarna </option>
    <option value="gorąca woda" selected="selected">Gorąca woda</option>
    <option value="czekolada">Czekolada</option>
    <option value="herbata">Herbata</option>
  </select>

```

### listy zagnieżdżone
```html
<optgroup label="title">
<!--lista wartości -->
</optgroup>

```

### Listy zagnieżdżone
`<select> <option>` definiuje istę wartości
Ta lista może być wielopoziomowa.
Kolejne poziomy tworzymy przy użyciu znacznika `<optgroup>`

ogólna postać
```html
<optgroup label="tytył danej grupy">
	<!-- lista wartości -->
</optgroup>

```
Dla każdego podmenu należy utworzyć przy użyciu znacznika `<option>` oddzielną listę wartości i przed nimi wstawić znacznik `<optgroup>`

```html
<form>
	<h3> Formularz wyboru przedmiotów <h3>
	<select name="wf" size=10 >
		<optgroup label="Basen">
			<option value="pływanie"> 
				Techniki pływania 
			</option>
			<option value="areobik wodny"> 
				Aerobik w wodzie 
			</option>
			<option value="nurkowanie"> 
				Techniki nurkowania 
			</option>
		</optgroup>

		<optgroup label="Sala gimnastyczna">
			<option value="koszykówka"> 
				Koszykówka
			</option>
			<option value="siatkówka"> 
				Siatkówka 
			</option>
			<option value="Piłka ręczna"> 
				Piłka ręczna 
			</option>
		</optgroup>

</form>


```


---

## TEXTAREA
pole do wprowadzania większej ilości tekstu
`<textarea>` może mieć atrybuty"
- `name="nazwa"` nazwa przypisana do pola
- `rows="n"` liczba wierszy w polu tekstowym
- `cols="n"` liczba kolumn(znaków) w polu tekstowym

postać ogólna
```html
<textarea name="nazwa" rows="n" cols="m"> 
	Tu wyświetlana wartość domyślna 
</textarea>
```

przykład
```html
<form>
	<h2>Twoje wrażenia po obejrzeniu ostatniej częśći Matrixa<h2>
	<textarea name="opinia" rows="8" cols="40"> Napisz swoją opinię
	</textarea>

</form>

```

---

## Nieaktywne pola formularza

`disabled`
jest nieaktywne

`readonly`
dla pól tekstowych, haseł, wyboru, bloków tekstu

```html
	<input readonly type=number value="123">
	<br>
	<button disabled> Wciśnij mnie </button>

```

---

## DATALIST
element autouzupełniania wartości wprowadzanych w `<input>`

```html
<form>
<p> Podaj preferowany środek transportu </p>
<input list="transport_do_wyboru" name="transport">
<datalist id="transport_do_wyboru">
	<option value="car">  </option>
	<option value="plane">  </option>
	<oprtion value="bike">  </option>
</datalist>

<input type="submit" value="Wyślij">


</form>


```



---
## ATRYBUTY

### autofocus
ustawia kursor w wybranym miejscu formularza, gdy strona zostanie załadowana

```html
<form >
		
<input type="text" name="imie" value="">
<br>
<br>

<input name="adres" type="text" autofocus>
</form>

```

### autocomplete -> wartości:  `on`   `off`
aby nie było możliwe autouzupełnianie
`<input type=text autocomplete="off">`


### required
Pole z tym atrybutem musi być wypełnione
```html
<form >
<lable> Wymagane		
<input type="text" name="imie" value="">
</lable>
<br>
<br>
<label for="zwykle_pole">Niewymagane</lable>
<input id="zwykle_pole" name="adres" type="text" autocomplete="off" required>
<br>
<input type="submit" value="Wyślij formularz">


</form>


```


### pattern
definuje wyrażenie regularne i sprawdza, czy wartość wprowadzona do pola jest zgodna z zadeklarowanym wyrażeniem
```html
<form >
<input title="nn-nnn" type="text" name="kod" pattern="[0-9]{2}-[0-9]{3}">
<br>
<input  type="submit" value="Wyślij formularz">


</form>
```


---

## ACTION i METHOD

patrz -> adres w przeglądarce po naciśnięciu przycisku "Submit"

z ustawionym atrybutem action na stronę i method na "get"
```html
<form action="https://www.wp.pl" method="get" >
<p> Podaj preferowany środek transportu </p>
<input list="transport_do_wyboru" name="transport">
<datalist id="transport_do_wyboru">
	<option value="car">  </option>
	<option value="plane">  </option>
	<oprtion value="bike">  </option>
</datalist>

<input type="submit" value="Wyślij">


</form>

```

method na 
[pst]
```html
<form action="https://www.wp.pl" method="post" >
<p> Podaj preferowany środek transportu </p>
<input list="transport_do_wyboru" name="transport">
<datalist id="transport_do_wyboru">
	<option value="car">  </option>
	<option value="plane">  </option>
	<oprtion value="bike">  </option>
</datalist>

<input type="submit" value="Wyślij">


</form>

```

Mejl
```html
<form>  
<p>Wysyłanie adresu mejl</p>
	<input type="email" name="useremail" value="">  
	<input type="submit" name=" " value="Submit">  
</form>

</form>

```

