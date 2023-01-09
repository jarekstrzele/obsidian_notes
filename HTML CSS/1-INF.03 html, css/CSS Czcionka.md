[[_ CSS]]

---
# Czcionka i tekst CSS

## CZCIONKA / FONT

- rodzina czcionki `font-family`
- styl czcionki `font-style`
- rozmiar czcionki `font-size`
- pogrubienie czcionki `font-weight`


### rodzaje czcionki
Ponieważ nie wszystkie rodzaje czcionek mogą być dostępnie, definiuje się listę czcionek (przeglądarka będzie przechodzi od pierwszej nazwy czcionki do ostatniej, aż znajdzie dany rodzaj czcionki)

`selector {font-family: rodz1, rodza2, ...;}`
`.moja_klasa {  font-family: "Times New Roman", Times, serif;}`

>wielowyrazowe nazwy czcionki umieszczamy w cudzysłowie np. "Times New Roman"

Nazwy rodzin czcionek:
- `serif` czcionki szeryfowe, litery i cyfry mają wykończenia: Times New Roman, Georgia, Bodoni, ...
- `sans-serif` czcionki bezszeryfowe (proste końcówki): Arial, Verdana, Futura, ...
- `monospace` czcionki monotypiczne, czyli znaki mają stałą szerokość: Courier, New Courier, ...
- `cursive` czcionki pochyłe: Comic Sans, Florence, ...
- `fantasy` czcionki dekoracyjne: Impact, OldTown, ...

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  
  <title></title>
  <style>
    p {
      font-size: 18px;
      color: green;
    }
  </style>
</head>
<body>
  To jest tekst poza paragrafem.
  <p> TO JEST TEKST W paragrafi </p>
  <p style="font-family: Georgia;"> font-family: Georiga </p>
  
  <p style="font-family: Arial;"> font-family: Arial </p>
  <p style="font-family: Courier;"> font-family: Courier </p>
  <p style="font-family: 'Monotype Corsiva';"> font-family: Monotype Corsiva </p>
  <p style="font-family: Papyrus;"> font-family: Papyrus </p>



</body>
</html>
```


__bezpieczne czcionki__ dla HTML i CSS:
-   Arial (sans-serif)
-   Verdana (sans-serif)
-   Helvetica (sans-serif)
-   Tahoma (sans-serif)
-   Trebuchet MS (sans-serif)
-   Times New Roman (serif)
-   Georgia (serif)
-   Garamond (serif)
-   Courier New (monospace)
-   Brush Script MT (cursive)

---

#### rozmiar czcionki
`selector {font-size: size;}`

Sposoby ustawiania wielkości czcionki:
1. __Za pomocą słów kluczowych__
`xx-small  x-small  small`
`medium`
`large   x-large   xx-large`

2. **Za pomocą wartości względnych**
`smaller` czcionka mniejsza od bieżącej
`larger` czcionka większa od bieżącej

3. **Za pomocą wartości podanych w jednostkach miary**
`px  pt  cm  in  mm  pc  em`

4. __Za pomocą wielkości procentowej__
`100%   23% ...`

5. __Za pomocą responsywnego rozmiaru czcionki__
jednostka `vw` (*viewport width*) `1vw` = `1%` szerokości okna, w którym wyświetlana jest w strona

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  
  <title></title>

</head>
<body>
  <h1> Za pomocą słów kluczowych </h1>
  <p style="font-family: Arial; font-size: xx-small"> Arial xx-small</p>
  <p style="font-family: Arial; font-size: xx-large"> Arial xx-large </p>
  <hr>
  
  <h1> Za pomocą wartości względnych <h1>
  <p style="font-family: Garamond; font-size:smaller"> Garamond </p>
  <p style="font-family: 'Times New Roman'; font-size:larger"> Times New Roman </p>
    <hr>
    
  <h1>Za pomocą jednostek miary <h1>
  <p style="font-family: 'Monotype Corsiva'; font-size: 22px">22px Monotype Corsiva </p>
  <p style="font-family: Papyrus; font-size: 22pt"> 22pt Papyrus </p>


      <hr>
   
  <h1>Za pomocą procentów <h1>
  <p style="font-family: 'Helvetica'; font-size:100%">100% Helvetica </p>
  <p style="font-family: Tahoma; font-size: 50%"> 50% Tahoma </p>
       <p style="font-family: 'Helvetica'; font-size:150%">150% Helvetica </p>
      
      <hr>
   <h1>Za pomocą responsywnego rozmiaru czcionki <h1>
  <p style="font-family: 'Georgia'; font-size:18px">18px Georgia </p>
  <p style="font-family:  'Trebuchet MS'; font-size: 5vw">5vw  Trebuchet MS </p>
  <p style="font-family: 'Brush Script MT '; font-size:10vw">10vw Brush Script MT  </p>
      
</body>
</html>
```


---

### style i warianty
#### style
`selector {font-style: style;}`

rodzaje stylów:
- `normal`
- `italic`
- `oblique` pochylona czcionka, może być wygenerowana przez pochylenie zwykłej czcionki

#### warianty
`selector {font-variant: value;}`

value:
- `normal`
- `small-caps` kapitaliki


```html
  <p style="font-family: Arial; "> Arial <p>
  <p style="font-family: Arial; font-style: normal"> Arial normal <p>
  <p style="font-family: Arial; font-style:italic"> Arial italic<p>
  <p style="font-family: Arial; font-style:oblique "> Arial oblique <p>
   <p style="font-family: Arial; font-variant: normal "> Arial normal <p>
    <p style="font-family: Arial; font-variant: small-caps "> Arial small-caps <p>

```

---

### waga 
`selector{font-weight: value;}`

value:
- `normal`
- `bold`
- `100 200 300 400` (normalna)
- `500 600 700` (bold)
- `800 900`
- `lighter`
- `bolder`

```html
  <p style="font-family: 'Courier New'; "> Courier New <p>
  <p style="font-family: 'Courier New'; font-weight: normal"> Courier New  normal<p>
  <p style="font-family: 'Courier New'; font-weight:bold"> Courier New bold<p>
  <p style="font-family: 'Courier New'; font-weight:100 ">Courier New 100<p>
  
    <p style="font-family: 'Courier New'; font-weight: 900 "> Courier New 900<p>
    <p style="font-family: 'Courier New'; font-weight: lighter "> Courier New lighter<p>
    <p style="font-family: 'Courier New'; font-weight: bolder "> Courier New lighter<p>

```
----

# Wszystkie atrybuty w jednym `font`
`selector{font: value;}`
`<p style="font: italic bold 12pt Georgia">`

należy zachować kolejność 
wartości dla `size` i `family` są wymagane




