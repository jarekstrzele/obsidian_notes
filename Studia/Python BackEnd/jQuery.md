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
    - Przykład użycia: `a[hreflang*='pl']`
    - Odnajduje elementy, których atrybut zawiera określony fragment, gdziekolwiek wewnątrz atrybutu.
    - Na przykład `<a hreflang="pl">`, `<a hreflang="en-pl">`
    - Nie wymaga, aby fragment był oddzielony od reszty atrybutu żadnym konkretnym znakiem.
2. `|` (kreska pionowa):
    - Przykład użycia: `a[hreflang|='pl']`
    - Odnajduje elementy, których atrybut jest równy określonemu wartości lub zaczyna się od niej i jest połączony z myślnikiem.
    - Na przykład `<a hreflang="pl">`, `<a hreflang="pl-PL">`, `<a hreflang="pl-xyz">`
    - Przyjmuje tylko wartości, które są dokładnym dopasowaniem lub zaczynają się od wartości, po której następuje myślnik.
3. `~` (tylda):
    - Przykład użycia: `a[hreflang~='pl']`
    - Odnajduje elementy, których atrybut zawiera określone słowo, niezależnie od pozycji słowa wewnątrz atrybutu.
    - Na przykład `<a hreflang="en pl">`, `<a hreflang="de pl it">`, `<a hreflang="xyzpl">`
    - Przyjmuje wartości, które są oddzielone spacją i zawierają określone słowo.




