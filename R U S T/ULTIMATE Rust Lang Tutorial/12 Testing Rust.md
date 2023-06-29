#rust/test 
`cargo new adder --lib`

Functions are tests, if they have an attribute `#[test]`.

`cargo test`

`lib.rs`
```rust
#[derive(Debug)]
struct Rectangle {
	width: u32,
	height: u32,
}

impl Rectangle{
	fn can_hold(&self, other: &Rectangle) -> bool{
	self.width > other.width && self.height > other.height
	}
}

#[cfg(test)]
mod tests {
	use super::*;

	#[test]
	fn larger_can_hold_smaller(){
		let larger = Rectangle{
			width: 8,
			height:7,
		};
		let smaller = Rectangle{
			width: 5,
			height: 1,
		};
	
		assert!(larger.can_hold(&smaller)) ;
	}

	#[test]
	fn smaller_can_hold_larger(){
		let larger = Rectangle{
			width: 8,
			height:7,
		};
		let smaller = Rectangle{
			width: 5,
			height: 1,
		};
	
	assert!(!smaller.can_hold(&smaller)) ;
	}
}
```

`assert_eq!(arg1, arg2)`
`assert_ne!(arg1, arg2)`


```rust
  

pub fn greeting(name: &str) -> String{

format!("Hello {}", name)

}

  

#[cfg(test)]

mod tests {

use super::*;

  

#[test]

fn greeting_contains_name(){

let result = greeting("Carol") ;

assert!(

result.contains("Carolll"),

"Greeting did not contain name, value was `{}`",

result

) ;

}

}

```













