#rust/variable 
[[_ Full Rust Beginners Cours]]


# declaration
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
	assert_eq!(x,12) ; // false

	//shadowing
	let x = 10 ;
	assert_eq!(x, 10) ; //true
}
```

# unused vars
```rust
fn main(){
	let x = 1 ;
}
// waring about unused variable x

fn main(){
	let _x = 1;
}
// no warings

// O R
#[alow(unsued_variables)]
fn main(){
	let x = 1;
}
// no warings
```

# Destructuring
```rust
fn main(){
 let (mut x, y) = (1,2) ;
	x += 2;

 assert_eq!(x, 3) ; //true
 assert_eq!(y, 2) ; // true
}
```

**destructuring assignments** (Rust 1.59)
```rust
fn main(){
	let (x,y) ; //declares two vars at once
	(x, ..) = (3,4) ; // x = 3
	[..,y] = [1,2] ; //  y = 2
	assert_eq!([x,y], [3,2]) ; // true


}
```

