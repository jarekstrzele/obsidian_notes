#rust/string 

- two commonly use types of strings
	- `String` - owned
	- `&str` - borrowed `String` slice
- Must use an owned`String` to store in a `struct`
- use `&str` when passing to a function

```rust
fn print_it(data: &str){
	println!("{:?}", data) ;
}

fn main(){
	print_it("a string slice") ; // is automatically borrowed
	let owned_string = "owned string".to_owned() ;
	let another_owned = String::from("another") ;
	print_it(&owned_string) ;
	print_it(&another_owned) ;
}
```














