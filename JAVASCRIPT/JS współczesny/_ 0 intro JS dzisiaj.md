#javascript 

# Preinstalacja
Potrzebny
- *NodeJS*
- VS Code
- inicjalizacja projektu npm `npm init`
- aby sformatować kod `npm install eslint --save-dev`
- inicjalizacja `eslinta`   to   `npx eslint--init`
- w pliku 'package.json' dodajemy `"type":"module"`, aby obsługiwane były moduły
- instalujemy pakiet z serwerem `npm install -g http-server` (-g  czyli globalnie)
- uruchom serwer z plikami z bierzącego folderu `http-server .`
- 

# Babel
"Babel" is a JavaScript compiler
https://babeljs.io
aby integrować Babel z projektem
`npm install --save-dev @babel/core @babel/cli`


----

# Zmienne i stałe
- użycie `var` sprawiało kłopoty (elementy własnościami obiektu `window`, użyte w pętli generewało kod z błędami semantycznymi
- `let` zmienna zadeklarowana z tym słowem "istnieje" w danym ograniczynym zakresie  (np. tylko wewnątrz funkcji, w której została zadeklarowana)

przykłady z konsoli
```javascript
var q =100
undefined
q
100
window.q 
100
let qq = 100
undefined
qq
100
window.qq 
undefined
```
zmienna zadeklarowana przez `let` nie może być znowy zadelarowana, ale jej wartość może ulec zmianie

`const i = 10;` stała wartość `i`
`const lista = [];` -> `lista.push(20)` bez problemu doda nową wartość do listy;  zmiennej `lista` nie mogę przypisać nowej listy, czy też jakiejkolwiek innej wartośći

## Funkcje strzałkowe
```javascript
const ret = [1, 0, 4, 0].filter(function (value) { return value > 0; });

// funkcja strzałkowa
const ret = [1, 0, 4, 0].filter(value => value > 0);
```

gdy więcej niż jeden argument, a ciało funkcji ma więcej niż jedną komendę
```javascript
(val1, val2) => {
	let sum = val1+val2;
	return sum;
```

gdy chcemy zwrócić obiekt
```javascript
(val1, val2) => ({
		"imie": val1,
		"wiek": val2
	})
```

### this








