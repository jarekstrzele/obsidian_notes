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

```rust
pub struct Guess {
	value: i32,
}

impl Guess {
	pub fn new(value: i32) -> Guess{
		if value < 1 || value > 100 {
		panic!("Guess value must be between 1 and 100, ") ;
	}
	Guess{ value }
	}
}

#[cfg(test)]
mod tests {
	use super::*;

	#[test]
	#[should_panic]
	fn greater_than_100(){
		Guess::new(200) ;
	}
}
```

## test returing `Result`

`()` unit type, nothing
```rust
#[cfg(test)]
mod tests {

#[test]
	fn it_works() -> Result<(), String>{
		if 2+2==4{
			Ok(())
		} else {
			Err(String::from("two plus two does not equal four"))
		}
	}

	#[test]
	fn it_works2(){
		assert_eq!(2+2, 4) ;
	}
}
```

------------
##### `--` każdy element po tym znaku będzie argumentem a nie opcją

##### `cargo test -- --help`  pomoc dla samych testów

##### `cargo test --help` pomoc na temat opcji dla `carg test`


`cargo test -- --test-threads=2`  - sometimes resolves problems with tests that have to be run paralel

### ` cargo test -- --show-output`
Opcja `--show-output` powoduje, że Cargo wyświetla wszystko, co zostało wypisane przez testy na standardowe wyjście, nawet jeśli testy przeszły pomyślnie.
> Opcja `--show-output` powoduje, że Cargo wyświetla wszystko, co zostało wypisane przez testy na standardowe wyjście, nawet jeśli testy przeszły pomyślnie.


### when you want to run   a specific test
```rust
pub fn add_two(a: i32) -> i32 {
	a + 2
}

#[cfg(test)]
mod my_tests{
	use super::*;

	#[test]
	fn add_two_and_two(){
		assert_eq!(4, add_two(2))
	}

	#[test]
	fn add_tree_and_two(){
		assert_eq!(5, add_two(3))
	}

	#[test]
	fn one_hundred(){
		assert_eq!(102, add_two(100))
	}
}
```


`cargo test <test_name>`
`cargo test add_two_and_two`

`cargo test <a_part_of_name_of_test>`
`cargo test add`

`cargo test <test_module_name>`
`cargo test my_tests`


## ignoring tests
```rust
#[cfg(test)]
mod tests {
	#[test]
	fn it_works(){
		assert_eq!(2+2, 4) ;
	}

	#[test]
	#[ignore]
	fn expensive_test(){
		// code that takes an hour to run
	}
}
```

## test organisation

>[!info] unit test
>It is a small focused test one module in isolation and could test private interface
>
>Unit test (**test jednostkowy**) to rodzaj testu oprogramowania, który polega na testowaniu pojedynczych, niezależnych jednostek kodu, takich jak funkcje, metody, klasy lub moduły. Celem testów jednostkowych jest zweryfikowanie, czy dane jednostki kodu działają zgodnie z oczekiwaniami, czyli czy zwracają poprawne wyniki dla różnych zestawów danych wejściowych oraz czy poprawnie obsługują różne przypadki brzegowe. 
>
>In Rust *unit test* lives  in the same file as our product code



>![info] integration tests
>it is a completely EXTERNAL to your library and thus test the public interface of your library
>
> [integration test](https://www.google.com/search?q=integration%20test) (**test integracyjny**) to rodzaj testu oprogramowania, który polega na testowaniu integracji między różnymi jednostkami kodu w celu weryfikacji, czy działają one razem zgodnie z oczekiwaniami. Testy integracyjne są ważne dla zapewnienia jakości oprogramowania i pozwalają na weryfikację interakcji między różnymi elementami systemu.
> 
> In Rust *integration tests*   lives in a a folder `tests` **at the root of your project



