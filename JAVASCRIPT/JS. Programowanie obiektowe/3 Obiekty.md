#javascript #oop #object 


# Tworzenie
**obiekt** jest dynamiczny (można go modyfikować w czasie wykonywania kody)

tworzenie obiektu za pomocą literału obiektu
```js
let jan = {
	imie: "Jan"
} ;
jan.imie = "Franek" ;
```

tworzenie obiekty za pomoca konstruktora `Object`
```js
let rambo = new Object() ;
rambo.imie = "Rambo" ;
```

właściwości zostały przypisane do konretnego obiektu


# Wykrywanie właściwości/atrybutów
Czy obiekt ma dany atrybut?
antywzorzec
```js
if (jan.wiek){ 
	//...
}
```
, bo jeżeli `jan.wiek===0`, to fałsz, czyli atrybut istniejący zostanie uznany za istniejący

poprawnie
```js
if ("wiek" in jan) { 
	//... 
}
```

tak samo z wykrywaniem metody
```js
if ('przedstawSie' in jan) {
	//...

}
```

Jeżeli chcemy odróżnić sytuację, że metoda przynależy tylko do obiektu, a nie również do prototypu `hasOwnProperty()`
```js
console.log("imie" in jan) ;
console.log(jan.hasOwnProperty("imie"))


console.log("toString" in jan) ; // true
console.log(jan.hasOwnProperty("toString")) //false
```

# Kasowanie atrybutów
`delete`

```js
delete jan.imie ;
```


# Wyliczenia
Atrybutu obiektu domyśłnie są wyliczalne (*enumarable*).
Pętla `for-in` przechodzi przez wszystkie atrybuty wyliczalne w obiekcie i w każdejiteracji przypisuje nazwę atrybutu do zmiennej
```js
for (var property in object){
	console.log("nazwa: "+ property) ;
	console.log("Wartość: " + object[property])
}
```
ten sposób iteruje po wszystkich atrybutach (zarówno instancji jak i prototypu)

Aby iterować wyłącznie po trybutach instancji: `Object.keys(objet)`


# Rodzaje właściwości
- właściwości danych ( `jakisObiekt.imie`)
- właściwości funkcji dostępowych:
```js
let rambo = {
	_name: 'Rambo',

	get name() {
		return this._name ;
	},

	set name(value){
		this._name = value ;
	}
}

console.log(rambo.name) ;
rambo.name="Potulny człowiek" ;
console.log(rambo.name) ;

```



# Zapobieganie modyfikowaniu obiektu
Obiekty mają wewnętrzne atrybuty.
Na przykład atrybut `Extensible` (domyślnie `true`) odpowiada za to, że obiekt jest rozszerzalny, a więc w dowolnej chwili można do nic dodawać nowe właściwości.

## Zapobieganie rozszerzeniu
`Object.preventExtensions(<obiekt, który ma być nierozszerzalny>)`
`Object.isExtensible(<obiekt do sprawdzenia>)`

```js
let kot = {
  name : "Miałczek"
}

console.log(Object.isExtensible(kot));
kot.sayHi = function (){console.log("Hiii");}
kot.sayHi()
Object.preventExtensions(kot) ;
console.log(Object.isExtensible(kot));
kot.age=123 ;
console.log("age" in kot) ;
kot.name = "Reksio" ;
console.log(kot.name) ;
```

## Pieczętowanie  obiektu
pieczętowanie *seal*
Nie tylko nie będzie można go rozszerzyć, ale i usuwać już istniejące właściwości/atrybuty.
`Object.isSealed(<obiekt do sprawdzenia>) ;`
`Object.seal(<obiekt do zapięczetowania>) ;`

```js
let chleb = {
	rodzaj: "Baltonowski"
}

console.log(Object.isExtensible(chleb)) ;
console.log(Object.isSealed(chleb)) ;

Object.seal(chleb);

console.log(Object.isExtensible(chleb)) ;
console.log(Object.isSealed(chleb)) ;

chleb.rodzaj = "Dwa razy pieczony" ;
console.log(chleb.rodzaj) ;
chleb.stan = "świeży" ;
console.log("stan" in chleb) ;

delete chleb.rodzaj ;

```
## Zamrażanie obiektu
*freeze*
Nie można:
- dodawać usuwać właściwości
- zmieniać typu
- zapisywać wartości do atrybutów

Niezmienialny obiekt tylko do odczytu.

`Object.isFrozen(<obiekt do sprawdzenia>) ;`
`Object.freeze(<obiekt do zamrożenia>) ;`

```js
let foka = {
	typ: "strunowce"
}

console.log(Object.isExtensible(foka)) ;
console.log(Object.isSealed(foka)) ;
console.log(Object.isFrozen(foka)) ;

Object.freeze(foka) ;
console.log("Extensible: ", Object.isExtensible(foka)) ;
console.log("Sealed: ", Object.isSealed(foka)) ;
console.log("Frozen: ", Object.isFrozen(foka)) ;

//foka.twojTyp(){console.log(this.typ) ;}
console.log(foka.typ) ;
foka.typ = "strunowiec z kosmosu" ;
console.log(foka.typ) ;
delete foka.typ ;
console.log("typ" in foka) ;
```






















