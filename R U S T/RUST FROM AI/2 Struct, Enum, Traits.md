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







