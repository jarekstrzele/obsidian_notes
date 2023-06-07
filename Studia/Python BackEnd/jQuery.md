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
	$("*").css({"border":"1px solid black", "backgroundColor":"grey"}) ;
</script>
</body>
</html>
```











