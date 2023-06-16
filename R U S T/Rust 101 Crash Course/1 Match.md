#rust/match 

==Match must be exhaustive==

```rust
fn main() {
	let some_bool = true ;
	match some_bool {
		true => println!("it's true"),
		false => println!("it's false"),
	}
}
```





