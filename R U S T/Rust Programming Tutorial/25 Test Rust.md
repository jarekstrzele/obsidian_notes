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


