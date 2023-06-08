
[[_ Ultimate Rust Crash Course]]

# Structs
#rust/struct 
In other languages  you have classes, in Rust you have `struct`
```rust
struct RedFox{
	enemy: bool,
	life: u8,
}
```
- structs can have data fields, methods, and associated functions
- structs are named *CamelCase*
- instantiating a struct yu need to specify a value for every single field
```rust
let fox = RedFox {
	enemy: true,
	life: 70,
}
```
you would implement an associated function to use as a CONSTRUCTOR to create a struct with default values
```rust
impl RedFox {
	fn new() -> Self{
		Self {
			enemy: true,
			life: 70,
		}
	}
}
```
`new()` is **an associated  function** (like *class method* in other languages )
`Self` can be used in place of the struct name

# Traits









# Collections





# Enum













