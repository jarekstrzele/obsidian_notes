#javascript #constructor #javascript/prototype 

>[!note] Konstruktor
>Funkcja, której używa się z operatorem `new` do utworzenia obiektu


Przykład (**nazwa konstruktura DUŻĄ LITERĄ**)
```js
function Person() {

}

let p1 = new Person ;
let p2 = new Person
```

`new` operator, który tworzy obiekt danego typu i zwraca go

```js
console.log( p1 instanceof Person) ;
console.log( p2 instanceof Person) ;
```

### atrybut `constructor`
Jest składnikiem wszystkich obiektów i zawiera referencję do funkcji konstruktora, za pomocą której obiekt został utworzony
```js
console.log( p1.constructor === Person) ;
console.log( p2.constructor === Person) ;
```

Konstruktor z parametrem 
```js
function Person(name){
	this.name=name ;
	this.sayName = function () {
		console.log(this.name)	
	}
}

let p1 = new Person("Jan") ;
let p2 = new Person("Wojtek") 
```

Każdy obiekt będzie miał swoją własną metodę `sayName` , czyli powtarzamy się (kod nie jest `DRY`)

# Prototypy
To przepis na obiekt.
Prawie wszystkie funkcje mają wbudowaną właściwość/atrybut `prototype` używaną podczas tworzenia nowych instancji.

==Prototyp== jest ==współdzielony== przez wszystkie obiekty danego typu.
Wszystkie obiekty danego typu mają dostęp do właściwości prototypu..

Ogólny typ `Object` ma metodę `hasOwnProperty()`, która jest zdefiniowana w prototypie. Każdy obiekt możne z niej korzystać tak, jakby była to metoda jego typu.

```javascript
var book = {
title: "The Principles of Object-Oriented JavaScript"
};
console.log("title" in book); // true
console.log(book.hasOwnProperty("title")); // true
console.log("hasOwnProperty" in book); // true
console.log(book.hasOwnProperty("hasOwnProperty")); // false
console.log(Object.prototype.hasOwnProperty("hasOwnProperty")); // true
```


## Właściowść `prototype`
Każda instancja przechowuje informację o swoim prototypie (w wewnętrznej właściowści `prototype`).
Gdy tworzony jest nowy obiekt danego typu, operator `new` przypisuje właściwość `prototype` konstruktora do właściwości `prototype` danego obiektu.

Aby zobaczyć atrybut `prototype` danego obiektu
```js
var object = {};
var prototype = Object.getPrototypeOf(object);
console.log(prototype === Object.prototype);

function Worm(name) { 
	this.name=name;
}

let w1 = new Worm('Idzi') ;
let w2 = new Worm('Pikaczu') ;

console.log(Object.getPrototypeOf(w1)) ;
console.log(Object.getPrototypeOf(w2)) ;
// prototypy obiektów wskazują na ten sam prototyp Person
```













Aby sprawdzić, czy dany obiekt jest prototypem innego obiektu:
`Object.prototype.isPrototypeOf(<obiekt do sprawdzenie>) ;`
```js
function Worm(name) { 
    this.name=name;
}

let w1 = new Worm('Idzi') ;
let w2 = new Worm('Pikaczu') ;

console.log(Object.getPrototypeOf(w1)) ;
console.log(Object.getPrototypeOf(w2)) ;

Object.prototype.isPrototypeOf(Worm)
true
Worm.prototype.isPrototypeOf(Object)
false
Worm.prototype.isPrototypeOf(w1)
true
Object.prototype.isPrototypeOf(w1)
true

```

Gdy JS poczukuje atrybutu, najpierw szuka wśród właściwości obiektu, potem, o ile nie znajdzie, w obiekcie prototypie, jeżeli nie znajdzie, zwraca `undefined` 
```js
var object = {};
console.log(object,toString()) //metoda z prototypu
object.toString = () => "nowa/przesłonięta funkcja toString()"
console.log(object,toString()) //metoda z prototypu
delete object.toString // kasuje tylko właściwości instancji, a nie atrybutu
console.log(object.toString())
```

Z poziomu intancji nie można przypisać wartości do właściowści prototypu.

## Używanie prototypów z konstrutorami
Jeżeli mamy metody wspólne dla wszystkich instancji danego typu, tworzenie kopii takich metod dla każdej instancji nie ma sensu.

Metody, które robią to samo, powinny być współdzielone przez wszystkie obiekty danego typu, a nie kopiowane dla wszystkich obiektów.

Użycie atrybutu `prototype`umożliwia tworzenie takich metod.
```js
function Person(name){
 this.name=name;
}

// umieszczenie metody sayName w prototypie a nie w konstruktorze
Person.prototype.sayName = () => console.log(this.name) ;
var p1 = new Person("Jan") ;
var p2 = new Person("Yui") ;

p1.sayName() ;
p2.sayName() ;

```
**Atrybuty** zdefiniowane w prototypie będą współdzielone przez wszystkie obiekty, więc atrybuty w własnościami referencyjnymi będą mogły być zmieniane przez wszystkie obiekty danego typu.
```js
function Person(name){
	this.name=name;
} ;

Person.prototype.myList=[] ; //referencyjny atrybut współdzielony

let p1=new Person("Ja") ;
let p2=new Person("Ono") ;

p1.myList.push("p1 added") ;
p2.myList.push("p2 added") ;

console.log(p1.myList) ;
console.log(p2.myList) ;

```












