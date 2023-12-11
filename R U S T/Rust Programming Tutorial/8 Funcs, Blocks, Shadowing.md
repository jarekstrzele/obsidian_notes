also see: [[9 Reference]]
[[_ Rust Programming Tutorial]]

```rust
fn main(){
	print_num_to(10);
}

fn print_num_to(num: u32){
	for n in 1..num{
		if is_even(n){
			println!("{} is even! ", n) ;
		}
		else {
			println!("{} is odd", n) ;
		}
	}

fn is_even(num: u32) -> bool{
	return num % 2 == 0 ;
}

}
```


---
# Blocks
```rust
fn main(){
	let x = 10 ;
	{
		let y = 20 ; //exists only in this block
		print("{}, {}", x, y) ;
		//isolated
	}
	// print("{}, {}", x, y)  --> error because `x` is not visible
	
}
```

----

# Shadowing

```rust
fn main(){
	let mut x = 10 ;
	{
		x=15 ;
	}
	println!("{}", x) //-> output 15

}
```

now shadowing:
```rust
fn main(){
	let mut x = 10 ;
	{
		let x=15 ;
	}
	println!("{}", x) //-> output 10

}
```

and one thing more -> change the type of the variable
```rust
fn main(){
	let mut x = 10 ;
	{
		let x=15 ;
	}
	println!("{}", x) //-> output 10
	
	let x = "it is a string" ;
	println!("{}", x) //-> it is a string

	let x = true ;
	println!("{}", x) //-> it is a string

}
```





