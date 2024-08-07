#jquery 

---
# Selectory

>[!info] selektory
>To specjalne znaki dodane w cudzysłowach pozwalają  nam wędrować po dokumencie
>przykładu:
>`*`
>`:animated`
>`:button`


## `traversing`
wędrowanie po dokumencie html
`add()` - możemy dotrzeć do konkretnego tagu html i dołączyć do niego jakiś nowy element
`Children()` pobiera elementy potomne względem danego znacznika html
`Each()` pętla, iterowanie po tak samo określonych elementach
`Not()` metoda, która usuwa elementy z wybranej grupy elementów
`Siblings()` w pamięci przeglądarki można określać style elementów z tej samej klasy
`...` 

## `events`
**zdarzenie** - rejestrowanie zachowania zewnętrznego (np. kliknięcie myszą) poprzez nasłuchiwanie interakcji między użytkownikiem a przeglądarką
`on()` podłączenie dowolnego zdarzenia
`blur()` zwolnienie elementu
`focus()` zaznaczanie elementu
`hover()` najeżdżanie na element (na, z)

## Ajax
umożliwia bardzo złożone asynchroniczne zapytania do serwera

----------
00:17:00
## `$(tagName).find("*").css({...})`
index.html
```html
<!DOCTYPE html>
<html>
<head>
<title>Selector All</title>
<link rel=""stylesheet" type="text/css" href="style.css" />
</head>

<body>
	<form id="form1" >
	<div id="d1"> </div>
	<div id="d2"> </div>
	<div class="clear"> </div>
	<div id="d3"> </div>
	<div id="d4"> </div>
</form>

<script src="https://code.jquery.com/jquery-3.7.0.min.js"></script>

<script>

//$("*").css("backgroundColor","red") ;
//$("*").css({"border":"1px solid black", "backgroundColor":"grey"}) ;
// $("#form1").find("*").css({"border":"1px solid black", "backgroundColor":"grey"})
$("#d1").find("*").css({"border":"1px solid black", "backgroundColor":"grey"}) ;

</script>
</body>
</html>
```


style.css
```css
.body{

}

.form {
	width:310;
	min-height:250px;
	margin-left: auto;
	margin-right: auto;
}

  

#d1, #d2, #d3, #d4 {
	float: left;
	width: 140px;
	height: 130px;
}

#d1{
	background-color: red;;
}

#d2{
	background-color: blue;;
}

#d3{
	background-color: forestgreen;;
}

#d4{
	background-color: aquamarine;
}

.clear{
	clear: both;
}
```


---------
## selector `animated`

style.css
```css
#main{
	width:400px;
	min-height:250px;
}

div{
	background-color: brown;
	border: 1px solid #aaa;
	width: 80px;
	height: 80px;
	margin: 0 5px;
	float: left;
}

div.colored {
	background:blue;
}

clear {
	clear:both;
}

button{
	display: block;
	width:400px;
	text-align: center;
}

h2 {
	text-align: center;
}
```

	` div.colored { background:blue;}` - It selects all `<div>` elements that have the class "colored".


index.html
```html
<!DOCTYPE html>
<html>
	<head>
	<title>Selector All</title>
	<link rel="stylesheet" type="text/css" href="style.css" />
</head>

<body>
	<div id="main" >
	<h2> Left Animated div </h2>
	<div></div>
	<div id="animated-div"></div>
	<div></div>
	<div></div>
	<p class="clear"></p>
	<button id="change">Change background color</button>
</div>

<script src="https://code.jquery.com/jquery-3.7.0.min.js"></script>
<script>
	$("#change").click(function(){
		console.log("click")
		$("div:animated").toggleClass("colored") ;
})

	function animate(){
		$("#animated-div").slideToggle(1500, animate) ;
}

	animate();

</script>
</body>
</html>
```

----------
# Attribute Selector
40 min.
fragment kodu
index.html
```html
<script src="https://code.jquery.com/jquery-3.7.0.min.js"></script>

<script>

//wybierze tag `a` w którego atrybucie wystęþuje "en" i zmień jego css

// $("a[hreflang|='en']" ).css("backgroundColor", "green") ;

//znajdzie podciąg pl

$("a[hreflang*='pl']").css("backgroundColor", "yellow") ;

</script>
```

1. `*` (gwiazdka):
    
    - Przykład: `div *`
    - Selektor dla wszystkich elementów potomnych dowolnego elementu.
    - Przykład: `div *` wybierze wszystkie elementy, które są potomkami elementu `<div>`.
2. `|` (kreska pionowa):
    
    - Przykład: `td|input`
    - Selektor dla elementów, które są w przestrzeni nazw określonej przez przedrostek przed kreską pionową.
    - Przykład: `td|input` wybierze wszystkie elementy `<input>`, które są wewnątrz elementu `<td>` w tej samej przestrzeni nazw.
3. `~` (tylda):
    
    - Przykład: `p ~ span`
    - Selektor dla elementów, które są rodzeństwem (mają tego samego rodzica) i znajdują się po nim.
    - Przykład: `p ~ span` wybierze wszystkie elementy `<span>`, które są rodzeństwem elementu `<p>` i występują po nim.
4. `$` (dolar):
    
    - Przykład: `a[href$='.pdf']`
    - Selektor dla elementów, których atrybut kończy się określonym ciągiem znaków.
    - Przykład: `a[href$='.pdf']` wybierze wszystkie elementy `<a>`, których atrybut `href` kończy się na `.pdf`.
5. `=` (równość):
    
    - Przykład: `input[type='text']`
    - Selektor dla elementów, których atrybut ma dokładnie określoną wartość.
    - Przykład: `input[type='text']` wybierze wszystkie elementy `<input>`, które mają atrybut `type` ustawiony na `'text'`.
6. `!` (negacja):
    
    - Przykład: `:not(.class)`
    - Selektor dla elementów, które nie pasują do określonego selektora.
    - Przykład: `:not(.class)` wybierze wszystkie elementy, które nie mają klasy `class`.

---
# Pseudo selektory
selektory poprzedzone wyłącznie znakiem `:`

> Znak `:` przed selektorem oznacza, że mamy do czynienia z selektorem pseudo-klasy, który jest wbudowany w język CSS i dostarczany przez bibliotekę jQuery. Selektory pseudo-klas są używane do wybrania elementów, które mają określone cechy lub są w określonym stanie.

```html
<script src="https://code.jquery.com/jquery-3.7.0.min.js"></script>

<script>

$(":button").css({

backgroundColor: "green",

color:"black",

border: "3px solid brown"

}) ;

$(":checkbox")

.wrap("<span></span>")

.parent()

.css({

backgroundColor: "green",

border: "3px red solid"

})

</script>
```







----------
# traversing
```html
<script src="https://code.jquery.com/jquery-3.7.0.min.js"></script>

<script>
	$(".main")
		.css({
			backgroundColor: "yellow",
			maringLeft ="auto"
		}).add("div")
		.css({
			border: "2px solid red",
			width: "60%",
		})

</script>
```


```html
<script src="https://code.jquery.com/jquery-3.7.0.min.js"></script>

<script>
	$(".div, div > p").addClass("border");
	$("div.before-addback").find("p").addClass("background");
	$("div.after-addback").find("p").addBack().addClass("background") ;
	

</script>
```

1. `<script src="https://code.jquery.com/jquery-3.7.0.min.js"></script>` - Ten wiersz importuje bibliotekę jQuery, umożliwiając korzystanie z jej funkcji i metod. Pobiera ona bibliotekę jQuery w wersji 3.7.0 ze zdalnego źródła przy użyciu podanego adresu URL.
    
2. `$(".div, div > p").addClass("border");` - Ta linia kodu dodaje klasę "border" do wszystkich elementów o klasie "div" oraz do wszystkich elementów `<p>`, które są bezpośrednimi potomkami elementów "div". W wyniku tego kodu, te elementy będą miały dodaną klasę "border", co może wpłynąć na ich stylizację za pomocą CSS.
    
3. `$("div.before-addback").find("p").addClass("background");` - Ta linia kodu znajduje wszystkie elementy `<p>` znajdujące się wewnątrz elementu o klasie "before-addback", a następnie dodaje im klasę "background". W rezultacie, elementy `<p>` wewnątrz tego konkretnego elementu "div" otrzymają klasę "background", co może wpływać na ich wygląd przy użyciu reguł CSS.
    
4. `$("div.after-addback").find("p").addBack().addClass("background");` - Ten fragment kodu znajduje wszystkie elementy `<p>` znajdujące się wewnątrz elementu o klasie "after-addback" i dodaje im klasę "background". Jednak w przeciwieństwie do poprzedniego przykładu, ta linia kodu zawiera również metodę `addBack()`. Metoda `addBack()` dodaje również oryginalny element, który był na stosie, do zbioru znalezionych elementów. W rezultacie, nie tylko elementy `<p>` wewnątrz elementu "div" o klasie "after-addback" otrzymają klasę "background", ale także sam element "div" otrzyma tę klasę.





