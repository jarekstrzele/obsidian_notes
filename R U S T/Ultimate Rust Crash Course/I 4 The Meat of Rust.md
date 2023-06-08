
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

to CREATE an instance of that struct:
```rust
let fox = RedFox::new();
let life_left = fox.life;
fox.enemy = false;
fox.some_method()
```
the scope operator in Rust is double colons `::`, and we use it to access parts of namespace-like things

METHODS are also DEFINED in the IMPLEMENTATION BLOCK:
```rust
impl RedFox{
	//associated function
	fn function() ...

	//method
	fn move(self) ..
	fn borrow(&self) ...
	fn mut_borrow(&mut self)
}
```

==NO STRUCT  INHERITANCE in Rust!!!!!==, because this gives us a better way to solve the problem we wish inheritance solved: TRAITS
#rust/traits 
==Rust takes the COMPOSITION over INHERITANCE APPROACH==


# Traits
>[!info] Trait
>- It is similar to in *interfaces* in other languages 
>-  it defines required behavior:
>		- finctions that struct must implement
>		- 

```rust
struct RedFox{
	enemy: bool,
	life: u8,
}

tait Noisy {
	fn get_noise(&self){...}
}
```








# Collections





# Enum













