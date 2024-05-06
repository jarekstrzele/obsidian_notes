#rust/struct 

# Struktury

>[!important]  **struktury**
> Pozwalają one na 
> > grupowanie różnych typów danych 
> 
> pod jedną nazwą.


```rust
struct Point{
	x: i32,
	y: i32
}

fn main() {

	let p = Point{x:10, y:20};
	println!("{}, {}", p.x, p.y);
}
```

# Enum
#rust/enum 
>[!important] `Enum`
>Wyliczenia (ang. *enums*) pozwalają na zdefiniowanie
>> typu, który może przyjmować różne warianty. 
> 
>Są one używane w wielu sytuacjach, gdzie struktury byłyby zbyt sztywne.


```rust
enum Message{
	Quit,
	Move {x: i32, y: i32},
	Write (String),
	ChangeColor(i32,i32,i32)
}

fn main() {
	let msg = Message::Quit;
	let msg1 = Message::ChangeColor(100,200,255);

	match msg1 {
		Message::Quit => println!("Wyjście"),
		Message::Move { x, y } => println!("Przesunięcie do ({}, {})", x, y),
		Message::Write(text) => println!("Wiadomość: {}!!", text),
		Message::ChangeColor(r, g,b ) => println!("Zmiana koloru na ({}, {}, {})", r, g, b)
	}
}
```



# `traits`
#rust/traits

>[!important] `traits`
>Cechy (ang. traits) to w pewnym sensie odpowiedniki interfejsów z innych języków, ale posiadają również inne możliwości. Pozwalają na definiowanie zbioru metod, które muszą być zaimplementowane przez struktury czy wyliczenia, które je implementują.

> Parametr `&self` oznacza, że metoda ma dostęp tylko do odczytu do struktury (nie może modyfikować pól).

```rust
use std::fmt::format;

trait Describable{
	fn describe(&self) -> String;
}

struct Animal{
	name: String,
	species: String,
	age: i32,
}


impl Describable for Animal{
	fn describe(&self) -> String {
		format!("{} jest zwierzęciem z gatunku {} i ma lat {}", self.name, self.species, self.age)
	}
}


fn main() {
	let my_pet = Animal {
		name: String::from("Burek"),
		species: String::from("Pies"),
		age: 11,
	};

	println!("{}", my_pet.describe());
}
```

>[!danger] `format!`
> Makro `format!` działa podobnie do `println!`, ale zamiast wypisywać wynik na standardowe wyjście, ==zwraca sformatowany łańcuch znaków== (`String`). 
> 
> Używane jest często do tworzenia tekstu, który później może być przetwarzany w inny sposób.


### Literały łańcuchowe i typ `String`

Rust rozróżnia dwa główne typy reprezentacji tekstu:

- **Literały łańcuchowe (`&str`)**: Są to niewielkie i niezmienne widoki na sekwencję znaków. Są zazwyczaj zapisywane bezpośrednio w kodzie jako ciągi znaków w cudzysłowach i są zapisywane w pamięci wykonywalnej programu.
- **Obiekty `String`**: Są to zmienne, dynamicznie alokowane ciągi znaków, które można modyfikować po utworzeniu (np. dodawać do nich inne ciągi, zmieniać je itp.). Są one bardziej elastyczne niż `&str` i używane, gdy potrzebujesz zmieniać tekst w trakcie działania programu.

# ZADANIA

## pierwsze - `struct`


>Utwórz strukturę `Car` reprezentującą samochód, która zawiera trzy pola: `make` (marka) typu `String`, `model` (model) typu `String`, oraz `year` (rok produkcji) typu `u32`. Następnie, w funkcji `main`, stwórz instancję tej struktury dla samochodu marki "Toyota", modelu "Corolla", z rokiem produkcji 2021. Wyświetl informacje o samochodzie w formacie: "Marka: Model (Rok produkcji)".


```rust
struct Car{
	make: String,
	model: String,
	year: u32
}

fn main(){

	let car = Car{make: String::from("Toyota"), model: String::from("Corolla"), year:2008};
	
	println!("Marka: {make}, Model: {model}, Year: {year}", make=car.make, model=car.model, year=car.year);
}
```

## drugie - `enum`
> Zdefiniuj wyliczenie `TrafficLight`, które reprezentuje sygnalizację świetlną z trzema możliwymi stanami: `Red`, `Yellow`, i `Green`. Napisz funkcję `print_signal`, która przyjmuje argument typu `TrafficLight` i wyświetla odpowiedni komunikat w zależności od stanu światła: "Stop" dla czerwonego, "Caution" dla żółtego, i "Go" dla zielonego.


```rust
enum TrafficLights{
	Red,
	Yellow,
	Green,
}

  

fn print_signal(light: &TrafficLights){
	match light{
		TrafficLights::Green => println!("Go"),
		TrafficLights::Yellow => println!("Caustion"),
		TrafficLights::Red => println!("Stop")
	}
}


fn main(){
	let light = TrafficLights::Yellow;
	print_signal(&light);
}
```



## trzecie - `traits`
> Zdefiniuj cechę `Printable`, która posiada metodę `print`. Metoda ta nie przyjmuje argumentów i niczego nie zwraca. Następnie zaimplementuj tę cechę dla struktury `Book`, która zawiera jedno pole `title` typu `String`. Implementacja metody `print` dla `Book` powinna wyświetlać tytuł książki. W funkcji `main`, stwórz instancję `Book` z tytułem "Rust Programming" i wywołaj metodę `print`.











