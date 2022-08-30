[[0-Wstęp do HTML, CSS tech]]

---
[[Elementy składowe strony WWW]]
[[CSS Selektory]]
[[CSS Czcionka]]
[[Model Blokowy CSS]]
[[CSS Marginesy]]
[[CSS rozmiar]]

---
# Kaskadowe arkusze stylów CSS

==CSS==
- odpowiedzialny jest za warstwę prezentacyjną strony
- określa układ graficzny dokumnetu HTML
- dostarcza bardzo dużo możliwości formatowania tekstu
- informacje dotyczące wyglądu dokumentu zapisane w oddzielnym pliku z rozszerzeniem `.css`
- jeden arkusz do wielu dokumentów
- pozwala na użycie różnych układów graficznych w zależności od typu urządzenia

---

## Wstawianie stylów

`selektor { właściwość: wartość; właściwość: wartość; ...}`
_selector_ określa  do jakich znaczników języka HTML odnosi się dalcza część definicji stylu (np. _p_, _body_, _h1_, ...)
_właściwość_ określa jaki atrybut znacznika będzie ustawiany (np. wielkość czcionki, tło, kolor, ...)
_wartość_ określa konkretną wartość atrybutu (np. 12pt, blue, ... )

### styl lokalny (w linii, _inline_)
- wsytępuje w pliku _.html_
czym mniej używany tym lepiej

```html
<p style="właściwość: wartość; właściwość: wartość"> ... </p>

<body style="background-color: black;"> ... </body>

<div style="właściwość: wartość; ..."> ... </div>
```

### wewnętrzny arkusz stylów
- między znacznikami `<style> ... </style>`
- w pliku _.html_

```html
<head>
...
	<style>
		p {color: orange;}
		h2 {color: blue; font-size: 18pt;}
		body {background-color: green;}
</head>
```

### zewnętrzny arkusz stylów
preferowany sposób formatowania stron WWW

w pliku _.html_ w sekcji `<head>`:
`<link rel="stylesheet" type="text/css" href="style.css">`

`<link>` tworzy relację między aktualnym dokumentem a zewnętrznym zasobem
`rel`  wartość tego atrybutu oznacza sposób, w jaki element, z którym jest powiązany, jest powiązany z dokumentem źródłowym. 
`type` z jakim typem danych jest powiązany dokument
`href` wskazuje na plik, z którym dokument jest powiązany

==od HTML5 wystarczy==:
`<link rel="stylesheet" href="style.css">`, bo CSS stał się domyślnym sposobem deklarowania stylów


w pliku _style.css_:
np.
```css
p {
	color: blue;
	font-size: 5;
	font-family: courier new;
}
```

---
## Ważność stylów - kaskadowość
Na jednej stronie wiele różnych stylów. Który styl "wybierze" przeglądarka?
(1 - najważniejszy, 7-najsłabszy)
1. `styl lokalny`
2. `<span>`
3. `<div>`
4. `<style>`
5. `<link rel="stylesheet ...>"`













