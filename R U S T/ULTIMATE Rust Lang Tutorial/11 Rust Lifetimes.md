https://www.youtube.com/watch?v=juIINGuZyBc&list=PLai5B987bZ9CoVR-QEIN9foz4QCJ0H2Y8&index=12

#rust/lifetimes
[[_ LetsGetRusty Ultimate Rust Lang Tutorial]]

-------
>[!info] lifetime of a variable
>a variable lives  inside its scope



>[!info] dangling reference
>It is a reference that points to invalid data 
>

example
```rust
fn main() {
	let r: &i32;

	{
		let x: i32 = 5;
		r = &x;
	}

	println!("r: {}", r) ; // generates an error
}
```
`x` - its lifetime ends with its scope









