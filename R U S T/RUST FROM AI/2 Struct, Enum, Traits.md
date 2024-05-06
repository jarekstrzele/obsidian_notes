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








