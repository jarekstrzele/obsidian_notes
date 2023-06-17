#rust/string 
>[!info] Strings
>- they are automatically borrowed
>- use `.to_owned()` or `String::from()` to create an owned copy of a string slice
>- use an owned `String` when string  in a `struct`



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


```rust
struct Employee{
	name: String,
}

fn main(){
	let emp_name = "Jayson".to_owned() ;
	// let emp_name = String::from("Jayson") ;
	let emp = Employee {
		name:emp_name
	} ;
}
```











