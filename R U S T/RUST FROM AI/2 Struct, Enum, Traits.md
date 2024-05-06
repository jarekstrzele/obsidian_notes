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





