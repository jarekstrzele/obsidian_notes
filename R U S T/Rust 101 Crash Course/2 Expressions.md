#rust/expression 
2:36:19
- Rust is an expression-based language (most things are evaluated and return some value)
- expression values coalesce to a single point (can be used for nesting logic)

```rust
enum Access {
	Admin,
	Manager,
	User,
	Guest,
}

fn main() {
	let access_level = Access::Guest ;
	let can_access_file = match access_level{
		Access::Admin => true,
		_ => false,
	} ;
	prinln!("can access: {:?}", can_access_file) ;
}


```



















