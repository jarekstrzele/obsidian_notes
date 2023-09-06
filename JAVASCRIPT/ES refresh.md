
----
# ES6 

## let var const
### `var` function scope
```javascript
function foo(){
  for (var i = 0; i < 5; i ++){
    console.log(i);
}

// i jest dostępna poza pętlą for
  console.log('i=',i);

foo();
```
output:
```bash
$ node index.js 
0
1
2
3
4
i= 5
```

### `let` block scope
```javascript
function foo(){
  for (let i = 0; i < 5; i ++){
    console.log(i);
}

// i jest dostępna poza pętlą for
  console.log('i=',i);

foo();

```

output
```bash
$ node index.js 
0
1
2
3
4
index.js:7
    console.log('i=',i);
                     ^

ReferenceError: i is not defined
```

### `const`
definiowanie stałej, ale jeżeli stała wskazuje na na przykład obiekt, to "wewnętrzne" elementy obiektu mogą ulegać zmianie
```javascript
const p = {"imie":"Jan"};
p["imie"] = "PIOTR";
console.log(p);
```

## Object
```javascript
// old way
const person = {
	name: "John",
	walk: function(){},
}

// new way
const person = {
	name: "John",
	walk (){},
}

person.walk();
person['name'] = "Jarek";
```

```javascript
const person = {
	name: "John",
	walk: function(){},
}
let a = "name";
console.log(person[a]);
```
output:
```bash
$ node index.js 
John
```

----
## `this` keyword
zawsze zwraca referencje do aktualnego obiektu
```python
const person = {
  name: "John",
  walk(){
    console.log(this);
  }
}
person.walk(); // this wskazuje na obiekt person
```
output
```bash
$ node index.js 
{ name: 'John', walk: [Function: walk] }
```

```javascript
const person = {
  name: "John",
  walk(){
    console.log(this);
  }
}

const walk = person.walk;
console.log("na co wskazuje 'walk'=", walk);
console.log("a teraz samo walk()");
walk();
```
output:
```bash
$ node index.js 
na co wskazuje 'walk'= [Function: walk]
a teraz samo walk()
<ref *1> Object [global] { //...
```
w drugim przypadku zwracany jest obiekt globalny (w przeglądarce to 'window')

## Jak poradzić sobie z tym problemem?
W JS funkcje są obiektem.
```javascript
const person = {
  name: "John",
  walk(){
  console.log(this);
  }
}

// 'bind' powiąże stałą 'walk' z 'this', czyli z obiektem person 
const walk = person.walk.bind(person);
console.log("na co wskazuje 'walk'=", walk);
console.log("a teraz samo walk()");
walk();
```
output
```bash
$ node index.js 
na co wskazuje 'walk'= [Function: bound walk]
a teraz samo walk()
{ name: 'John', walk: [Function: walk] }
```

----
## Arrow functions Funkcje strzałkowe
```javascript
const ret = [1, 0, 4, 0].filter(function (value) { return value > 0; });

// funkcja strzałkowa
const ret = [1, 0, 4, 0].filter(value => value > 0);
```

```javascript
const prace = [
  {id: 1, isActive: true},
  {id: 2, isActive: false},
  {id: 3, isActive: true}
];

console.log(prace.filter(function(praca) {
  return praca.isActive;
  } ));
```
output
```bash
$ node index.js 
[ { id: 1, isActive: true }, { id: 3, isActive: true } ]
```
ten sam wynik, ale przy użyciu arrow function
```javascript
console.log(prace.filter(praca=>praca.isActive));
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

### `this` i funkcje strzałkowe
```javascript
const kot = {
   mialcz(){
   setTimeout(function(){
   console.log("this = ", this);
   }, 1000)
 }
};

kot.mialcz();
```
output w przeglądarce
```bash
this =  Window {0: Window, 1: Window, window: Window, self: Window, document: document, name: '', location: Location, …}
```
output w terminalu
```bash
$ node index.js 
this =  Timeout { ....
```

przy użyciu arrow function
```javascript
const kot = {
  mialcz(){
  setTimeout(() => console.log("this = ", this)
   , 1000)
 }
};

kot.mialcz();
```
output w terminalu
```bash
$ node index.js 
this =  { mialcz: [Function: mialcz] }
```
output w przeglądarce
```bash
> kot.mialcz()
this =  {mialcz: ƒ}
```

---
## Array

### push(new_item)
```js
let  lista = [1,2,3];
lista.push("new item");
console.log(lista) // -> [1,2,3,"new item" ]

```
### unshift()
```js
tab1.unshift(elem) // -> dodaje elem na początek listy i istniejące elementy przesuwa o 1
```

### pop()
`tab1.pop()` -> zwraca ostatni element tablicy i usuwa ten element z tablicy  

### shift()
`tab1.shift()` -> zwraca pierwszy element tablicy i usuwa ten element z tablicy

### map()
mapowanie, przekształcanie, transformowanie jednej listy na inną zgodnie ze zdefiniowną funkcją

funkcja `map()` wraca nową listę
```javascript
const kolory = ['red', 'green', 'blue'];
const newList = kolory.map(kolor => '<li>' + kolor + '</liv>');
console.log(newList);
```
output
```bash
$ node index.js 
[ '<li>red</liv>', '<li>green</liv>', '<li>blue</liv>' ]
```

lepsza wersja z *template string*:
```javascript
const newList = kolory.map(kolor => `<li>${kolor}</liv>`);
```

---
# FOR
```js
for (let i=0; i< 5; i++){

    console.log(i);

}
```
## `for in` iterowanie po obiekcie
```js
for (let i in thisObject) {
// do something
}
```
```js
var pies = {imie:"Reksio", wiek: 5, miasto: "Olszyn"};

for(let k in pies) { console.log(k)}
```

## `forEach` 
```python
var mojaLista = [1,2, true, false, "Tom"]
mojaLista.forEach( (arg) => console.log(String(arg)+"200"))
```

## `for of`
`for (let i in someiterator) { //do something }`

```js
var mojaLista = [1,2, true, false, "Tom"]

for (let item in mojaLista){
  console.log(item);
  }
```

---
# Destructuring
## object
```javascript
const pies = {
	imie:"Reksio",
	wiek:5,
	plec:"samiec"
}

const imie = pies.imie;
const wiek = pies.wiek;
const plec = pies.plec;
console.log(imie,wiek,plec);
```

DESTRUKTURYZACJA `{  }`
`const {imie, wiek, plec} = pies;`

zmiana nazwy zmiennej
```js
const {imie: i, wiek: w, plec: p} = pies;
console.log(i,w,p);

```

```js
const printImie = ({imie}) => console.log(imie);
const printImieIWiek = ({imie, wiek}) => console.log(imie, wiek)

```

## array
```js
const hobbies = ['Sport', 'Cooking'];
const [hob1, hob2] = hobbies;
console.log(hob1, hob2);
```



## Spread Operator

### operator spread na liście
```javascript
const l1 = [1,2,3,4];
const l2 = ['a', 'b', 'c'];

const l1l20 = [l1, "nowy element", l2];

const l1l2 = [...l1, "nowy element", ...l2];

const clonel1 = [...l1];
console.log(l1l20);
console.log(l1l2);
console.log(clonel1);


```

### spread operator na obiekcie
```javascript
const w1 = {imie: "Gerald"};
const w2 = {zawod:"Wedźmin"};

const mieszaniec0 = {w1, w2, miejsce:"Olsztyn"}

const mieszaniec = {...w1, ...w2, miejsce:"Olsztyn"}

const clone = {...w1};
console.log(mieszaniec);
console.log(mieszaniec0);
console.log(clone);
```

## REST operator
przeciwieństwo `spread`
```js
const toArray = (...agrs) => {return args; }
// ... -> łączy wiele argumentów w jedną listę

const [a,b,c, ...rest] = [1,2,3,4,5,true,"string"]

```

---
# Klasy classes
```javascript
const person1 = {
	name: "Jan",
	walk(){
		console.log("walk")
	}
}
const person2 = {
	name: "Piotr",
	walk(){
		console.log("walk")
	}
}
```

#### ==DRY - Don't Repeate Yourself==
```javascript
class MyPerson{
	constructor(name){
		this.name=name;
	}
	walk(){
		console.log("walk");
	}
}

const person = new MyPerson("Jan");
```

#  Dziedziczenie Inheritance
```javascript
class MyPerson{
	constructor(name){
		this.name=name;
	}
	walk(){
		console.log("walk");
	}
}

class Uczen extends MyPerson{
  constructor(name, school){
    super(name);
    this.school = school;
  }
  
}

const janek = new Uczen("Jan", "Technikum");
console.log(janek);
```

---
## Modules
plik: myperson.js
```javascript
export class MyPerson{
	constructor(name){
		this.name=name;
	}
	walk(){
		console.log("walk");
	}
}
```
plik: uczen.js
```javascript
import { MyPerson } from './myperson.js'


class Uczen extends MyPerson{
  constructor(name, school){
    super(name);
    this.school = school;
  }
  
}
```
takie pliki są modułami i to co jest zdefiniowane w module domyślnie jest prywatne, czyli nie dostępne poza tym modułem/plikiem

aby fragment modułu "wystawić" na zewnątrz, trzeba go exportować, dlatego klasa `MyPerson` jest poprzedzona słowem `export`

### named export, default export

#### named export
one.js
```javascript
export function foo(){
	return 'foo';
}

export function kuu(){
	return 'kuu';
}
```

two.js
```javascript
import {foo, kuu} from "./one";
```

#### default export
one.js
```javascript
export default function foo(){
	return 'foo';
}

function kuu(){
	return 'kuu';
}
```
two.js
```javascript
import foo from "./one";
```
nie trzeba używać `{}`, bo default export może być tylko jeden,
ale `named` i `default` mogą występować razem
```javascript
export default function foo(){
	return 'foo';
}

export function kuu(){
	return 'kuu';
}
```
two.js
```javascript
import foo, {kuu} from "./one";
```


```javascript
import React, {Component} from 'react';
```
czyli `React` jest eksportem domyślnym, a `Component` jest *named export*

### Eksport na końcu pliku

*named export*
```javascript
function foo(){
	return 'foo';
}

function kuu(){
	return 'kuu';
}

export {foo, kuu};
```

*default export*
```javascript
function foo(){
	return 'foo';
}

function kuu(){
	return 'kuu';
}

export default foo;
```




