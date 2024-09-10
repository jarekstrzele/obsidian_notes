#javascript/evetnt 

[[DOM and Events]]

---

[[11.1 this]]
[[11.2 onload]]
[[11.3 nasłuchiwacz zdarzeń]]
[[11.4 obiekt Event]]
[[11.5 Propagacja eventów]]




# EVENTS
> **event**      to, co się dzieje na stronie, a my wskazujemy, jaka wówczas funkcja będzie wywołana; to aktywność użytkoników **DHTML**  

```html
<div onmouseover="alert('coś tam alert')">
	Coś tam kilknij 
</div>
//lepiej
<div id="test"> kliknij mnie </div>
```

```js
function foo(){
	alert("function");
	}
var test = document.getElementbyId("test");
test.onclick = foo;
/* jeżeli funkcja przyjmuje argumenty, trzeba zrobić funkcję anonimową
test.onclick = function (tekst) {
  alert(tekst);
}  
*/
```



