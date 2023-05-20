[[_ Rust Programming Tutorial]]

```rust
fn main() {
	let number = 12;

	match number {
		1 => println!("it is one"),
		2 => println!("there is two of them "),
		10 | 12 => println!("this is 10 or 12"),
		//14..20 => println!("it is between 14 and 20"), //doesn't work
		_ => println!("It doesn't match"),
	}

let name = "Domenic";
	match name {
		"Jan" => println!("Hey, Jan"),
		"Domenic" => println!("hii, Domenic"),
		_ => println!("Nothing"),
	}
}
```








