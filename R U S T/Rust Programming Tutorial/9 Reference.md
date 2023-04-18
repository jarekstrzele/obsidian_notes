#rust 

>[!info] reference
>It is just another way to refer to a variable


`&x` means you want to get a reference to the variable to `x`
```rust
fn main(){
	let mut x = 10;
	let xr = &x;
	let dom = &x;

	println!("x is {}", xr) ; // output `x is 10`
	println!("x is {}", dom) ; // output `x is 10`
	println!("x is {}", x) ; // output `x is 10`
}
```
we can use `xr` in the same way we use `x`



