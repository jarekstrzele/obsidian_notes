[[0-Wstęp do HTML, CSS tech]]


[[Elementy składowe strony WWW]]
[[Obrazy i odsyłacze]]
[[Formularze]]


# Struktura strony

>Dokument HTML to "ciąg" znaczników i ich zawartości,
Przeglądarka odczytuje znaczniki i "wie", jak wyświetlać teksty, obrazy, animacje, filmy

## Znaczniki
`<nazwa_znacznika>` - to polecenie odczytuje przeglądarka i odpowiednio wyświetla zawartość

```HTML
<!-- <znacznik_otwierający> zawartość  </znacznik_zamykający> 
-->
<p> To jest teść paragrafu </p>

```
### atrybuty znaczników
```HTML
<img src="moja_szkola.jpg" alt="szkoła" height="100" width="200">

```
`src` źródło
`alt` tekst wyświetlany, jeżeli obraz nie zostanie wczytany
`heigh` wysokośc obrazka
`width` szerokość obrazla

---

## Nagłówek
```html
<head> 
	<title> Tytuł </title>
	<meta name="description" content="Strona poświęciona iczemu >
</head>
```

### Znacznik `<meta>`
informuje: kto jest autorem, data utworzenia, kodowanie znaków
ma trzy atrybuty:
- `http-equiv`   informacje o stronie -> wartości:
	- `Content-Type` sposób kodowania znaków
	- `Content-Language` język dokumentu
	-  `Reply-to` e-mail autora
- `name` niezbędne dla wyszukiwarek informacje ->
	- `Title, page-topic` ustawia tytuł i  opis
	- `Creation_Date` ustawia datę utworzenia strony
	- `Keywords` definiuje słowa kluczowe
	- `Description` definiuje opis strony widoczny w wynikach wyszukiwania
	- `Robots` indeksowanie strony 
- `content`

`<meta http-equiv="Refresh" content="x">` strona będzie odświeżana co x sekund
`<meta http-equive="refresh" content="x; url=adres"> po x czasie strona przejdzie pod nowy adres

### Język dokumentu
`<html lang="pl-PL">` "pl" używany język "PL" kraj

### znacznik `<link>`
służy do dołączania do strony zewnętrznych plików
zwykle do dołączenia pliku CSS:

`<link rel="stylesheet" type="text/css" href="style.css">`

`rel` w jaki sposób plik będzie powiązany ze stroną
_stylesheet_ będzie to plik ze stylami


### Adres bazowy `<base>`
Definiujemy ten znacznik, aby działały relatywne odsyłacze.
Przeglądarka odczyta adres bazowy i będzie go używała, aby dookreśłić adresy relatywne

```html
<head> 
	<base href="http://www.abc.com>"
</head>
<body>
	<img src="img/moja_szkola.jp" alt="Moja szkoła" />

</body>

```

	<img src="http://abc.com/img/moja_szkola.jp" alt="Moja szkoła" />

### ciało dokumenty
`<body> content </body>`













