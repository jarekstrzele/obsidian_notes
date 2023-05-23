#rust/test
[[_ Rust Programming Tutorial]]

### `cargo test`

```rust
fn main() {

}

#[cfg(test)] // -> this attribute make that the module will not be compile, only test
mod decode_tests {
	#[test]
	#[should_panic]
	fn test_basic() {
		// pass something that has to be true
		assert!(1 == 1) ;
		panic!("Oh no") ; // fail the test, but attribute #[should_panic] makes the whole test will be ok
	}
}
```


to access out of the module use
#### `super::`

```rust
fn main() {
}

fn give_two() -> i32 {
	2
}

#[cfg(test)] // -> this attribute make that the module will not be compile, only test
mod decode_tests {

	#[test]
	#[should_panic]
	fn test_basic() {
		// pass something that has to be true
		assert!(1 == 1) ;
		panic!("Oh no") ; // fail the test, but attribute #[should_panic] makes the whole test will be ok
}

	#[test]
	#[ignore] // this function will not be tested
	fn test_equals(){
		assert_eq!(2, 1 + 1) ; //
		assert_ne!(2, 1 + 2) ;
	}

	#[test]
	fn test_equals_2(){
		assert_eq!(super::give_two(), 1 + 1) ; //
		assert_ne!(super::give_two(), 1 + 2) ;
	}

}
```


```rust
struct Rectangle {
	width: u8,
	height: u8,
}
	
impl Rectangle {
	fn is_square(&self) -> bool {
	self.width == self.height
	}
}

fn main() {
}

#[cfg(test)] // -> this attribute make that the module will not be compile, only test
mod decode_tests {
	#[test]
	#[should_panic]
	fn test_structs(){
		let r = super::Rectangle {
		width: 50,
		height: 50
	} ;

		assert!(r.is_square()) ;
	}
}
```
















