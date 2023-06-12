#rust #youtube  #zubi_aran
https://www.youtube.com/watch?v=_EREi8kJ8z8

# variable
```rust
let  x= 1 ; //immutable
let mut y = 1 ; // mutable

assert_eq!(y, 1) ;
```

# scope
```rust
fn main() {
	let x: i32 = 10;
	{
		let y: i32 = 5;
		
	}
	println!("{:?}", y) ; // error
	println!("{:?}", z) ; // erro
}

fn new_scope_z(){
	let z: &str = "Hello" ;
	
}
```

# shadowing
```rust
fn main() {
	let x = 5;
	{
		let x = 12;
		assert_eq!(x,12); //true
	}
	assert_eq(x,12) ; // false
	
	let x = 10 ;
	assert_eq(x, 10) ; //true
}
```


