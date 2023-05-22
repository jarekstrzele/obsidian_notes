#rust/input
```rust
use std::io;

fn main() {
	let mut input = String::new();
	println!("Hey mate! Say something: ") ;

//io::stdin() - call the input stream
//read_line() - call read line method od that stream
//read_line returns a Result: succ or fail
	match io::stdin().read_line(&mut input) {
		Ok(b) => {
			println!("Success! {}, and b: {}", input, b) ;
			println!("Success! Uppercase: {}", input.to_uppercase()) ;

},
	Err(e) => {println!("Opps! SOmething went wrong: {} ", e) ;}
}
}
```