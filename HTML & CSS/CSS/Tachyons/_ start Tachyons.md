[[CSS <-> Tachyons]]
[[Type Scale]]
[[padding and margin]]
[[Flex in Tachyons]]



---

http://tachyons.io/

# Tachyons
#tychons 
## to start
`<link rel="stylesheet" href="https://unpkg.com/tachyons@4.12.0/css/tachyons.min.css"/>`

or

`npm install tachyons@4.12.0`

```html
<!DOCTYPE html>
<html lang="en">
  <title> </title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://unpkg.com/tachyons/css/tachyons.min.css">
  <body>

  </body>
</html>
```

---
## Quick Introduction
https://tachyons.io/#style

### header
header -> f
`class="f1"`    `class="f4"` ... `f6`
f1 -> font-size:3rem
f2
f3
f4 -> font-size: 1.25
f5
f6

----
### style
.i {         font-style: italic; }
.b {         font-weight: bold; }
.underline { text-decoration: underline; }
.strike {    text-decoration: line-through; }
.ttc {       text-transform: capitalize; }
.ttu {       text-transform: uppercase; }

`<p class="f2 b i ttc"> a to sformatowany </p>`
` <p class="f4 ttu strike i"> a to sformatowany </p>`

```html
<div class="f3 code">
      to jest kod
 </div>
```

---
### typefaces
```css
.sans-serif {
  font-family: -apple-system, BlinkMacSystemFont,
               'avenir next', avenir,
               helvetica, 'helvetica neue',
               ubuntu,
               roboto, noto,
               'segoe ui', arial,
               sans-serif;
}
.serif { font-family: georgia, times, serif; }
.code { font-family: Consolas, monaco, monospace; }
.courier { font-family: 'Courier Next', courier, monospace; }
.helvetica { font-family: 'helvetica neue', helvetica, sans-serif; }
.avenir { font-family: 'avenir next', avenir, sans-serif; }
.athelas { font-family: athelas, georgia, serif; }
.georgia { font-family: georgia, serif; }
.times { font-family: times, serif; }
.bodoni { font-family: "Bodoni MT", serif; }
.calisto { font-family: "Calisto MT", serif; }
.garamond { font-family: garamond, serif; }
.baskerville { font-family: baskerville, serif; }
```

```html
   <article class="athelas f3 b underline">
      to jest kod
    </article>
    
```

### border
```html
<div class="ba bw2">
    <article class="code f2 ">
      to jest kod
    </article>
</div>
```

`ba` - border all
(`ba`   `bt` (top)   `br`(right)   `bl` (left)   `bb` (bottom)   `bn`(none) )
`bw2` - border-width: 25rem
(bw0 ... bw5)

```css
.b--dotted { border-style: dotted; }
.b--dashed { border-style: dashed; }
.b--solid {  border-style: solid; }
.b--none {   border-style: none; }
```

#### Border radii
`<button class="ba f1 bw3 br4"> to jest  2 </buttom> `

`<button class="br-pill  f2 code bw3  b--green dark-pink bg-yellow"> to jest ONE </buttom>`

```css
.br0 {        border-radius: 0; }
.br1 {        border-radius: .125rem; }
.br2 {        border-radius: .25rem; }
.br3 {        border-radius: .5rem; }
.br4 {        border-radius: 1rem; }
.br-100 {     border-radius: 100%; }
.br-pill {    border-radius: 9999px; }
.br--bottom {
    border-top-left-radius: 0;
    border-top-right-radius: 0;
}
.br--top {
    border-bottom-left-radius: 0;
    border-bottom-right-radius: 0;
}
.br--right {
    border-top-left-radius: 0;
    border-bottom-left-radius: 0;
}
.br--left {
    border-top-right-radius: 0;
    border-bottom-right-radius: 0;
}


```

`<button class="br-pill br--right  f2 code bw3  b--green dark-pink bg-yellow"> to jest ONE </buttom>`

---
### colors
bg - background
`bg-green` == `background-color: green;`

```css
.bg-dark-red { background-color: var(--dark-red); }
.bg-red { background-color: var(--red); }
.bg-orange { background-color: var(--orange); }
.bg-gold { background-color: var(--gold); }
...
```

function `var()`:
(*var* <->*variable*) pozwala używać zmiennych, które przechowują pewne wartości
```css
:root{
	--my-color: black;
}

p{
background-color: var(--my-color);
}
```

```html
 <h1 class="bg-purple light-blue"> to jest ha1</h1>
 <p class="f2 b light-red"> a to sformatowany </p>
 <div class="ba bw2">
    <article class="code f2 bg-red blue ">
      to jest kod
    </article>
 </div>
```

```css
.b--black-90 {   border-color: var(--black-90); }
.b--black-80 {   border-color: var(--black-80); }
.b--black-70 {   border-color: var(--black-70); }
.b--black-60 {   border-color: var(--black-60); }
.b--black-50 {   border-color: var(--black-50); }

...
```

---
## hover animations
```html

    <button class="grow br-pill br--right  2 code bw3  b--green dark-pink bg-yellow"> to jest ONE </buttom> 
    </button>
 <p class="dim"> to jest lorem ipsum ali teri kooo </p>   
    
    
```

---
## GRIDS
### floats, widths, padding
`fl w-number` 
`fl w-100`
`fl w-60    fl w-40`

`fl w-third    fl w-third     fl w-third`
`fl w-third   fl w-two-thirds`

---
## dodatkowe info o float CSS
#### float (unoszenie się elementu)
służy do formatowania miejsca zawartości w elemencie (np. obrazek po lewej, tekst po prawej)
`float: value`

`value`:
- `left`
- `right`
- `none` (by default)
- `inherit`

ustawienie `div`ów obok siebie
```css
div {
	float:left;
	padding: 10px;
}
```

#### clear
`clear` ustala, jak ma być wyświetlony element po elemencie z `float`
`clear: value`

`value`:
- `none` by default
- `left` element będzie ustawiony pod elementem z `float: left`
- `right`
- `both` element będzi ustawion pod elementem, który ma ustwiony `float` na `left` lub `right`
- `inherit` wartość `clear ` będzie dziedziczona po rodzicu

gdy element wykracza poza swoje "pudełko"
```css
.clearfix::after {
  content: "";
  clear: both;
  display: table;
}
```

`content` jest uzywany z `::before` lub `::after`