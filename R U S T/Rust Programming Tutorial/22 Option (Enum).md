#rust/option #rust/enum 
[[5 Enum]]

#### `Option` represents either **a value** (**Some( )**) or **no value** (**None**)

Many functions in Rust return `Option` (e.g.  you want to get  fifth character of word but that word has only three character, so Rust returns `Option` not a character itself)

```rust
fn main() {
	let name = String::from("Domenic") ;
	// chars() returns an iterator over all the characters in this string
	// nth(index) returns an item at the index that you pass it
	// chars().nth(index) returns an Option
	println!("Character at index 8: {} ", match name.chars().nth(0){
		Some(c) => c.to_string(),
		None => "No character at index 8".to_string()
});
}
```


```rust
fn main() {
	println!("Occupation is {} ", match get_occupation("Domenic"){
		Some(o) => o,
		None => "No occupation found",
	})
}

 
fn get_occupation(name: &str) -> Option<&str> {
	match name {
		"Domenic" => Some("Software Developer"),
		"Michael" => Some("Dentist"),
		_ => None,
	}
}
```







