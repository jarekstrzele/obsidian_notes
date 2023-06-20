#rust #youtube 
https://www.youtube.com/watch?v=ygL_xcavzQ4

#### `cargo new rust_tutorial`

at the beginning of a file write
### `#![allow(unsused)]`

`use std::io ;` 
`use std::io::{Write, BufReader, BufRead, ErrorKind} ;`
`use std::fs::File ;`
`use std::cmp::Ordering ;`

`use rand::Rng ;` random numbers ==> this line of the code generates an error, so
go to `Cargo.toml` file and under `[dependecies]` put `rand = "0.8.5"`

vs code - `rust-analyzer`

https://crates.io/

----------
# app 'what is your name'

```rust
fn main() {
	println!("What is your name?") ;
	let mut name = String::new() ;
	io::stdin().read_line(&mut name).expect("Didn't Receive Input") ;
	println!("Hello, world!");
}
```

`&mut name` this is a reference to a variable
`read_line` returns `Result`
`Result` it is a `enum` and *enum* it is a type that has a fixed number of possible values
*Result* can return `Ok` or `Err`

```rust
fn main() {
	println!("What is your name?") ;
	let mut name = String::new() ;
	let greeting = "Nice to meet you" ;
	io::stdin().read_line(&mut name).expect("Didn't Receive Input") ;
	println!("Hello, {}! {}", name.trim_end(), greeting);
}
```

--------
# Constant
`const ONE_MIL: u32 = 1_000_000 ;`
`const PI: f32 = 3141592 ;`

---
# shadowing
define variables with the same name but different data types
```rust
let age: &str = "47" ;
let mut age: u32 = age.trim().parse().expect("Age was't assigne a number") ;
age = age + 1;
println!("I'm {} and I want ${}", age, ONE_MIL)

```

----
# Types
Rust is **statically typed** which means all the types must be defined (compiler will defined them or you define them)


```rust
fn main() {
	println!("Max u32: {}", u32::MAX) ;
	println!("Max u64: {}", u64::MAX) ;
	println!("Max u128: {}", u128::MAX) ;
	println!("Max f32: {}", f32::MAX) ;
	println!("Max f128: {}", f64::MAX) ;
}

output
Max u32: 4294967295
Max u64: 18446744073709551615
Max u128: 340282366920938463463374607431768211455
Max f32: 340282350000000000000000000000000000000
Max f128: 179769313486231570000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
 *  Terminal will be reused by tasks, press any key to close it. 
```


`f32`
`f64`
`u32`
`u64`

---
```rust
use rand::Rng ;


fn main() {
	let random_num: i32 = rand::thread_rng().gen_range(1..6+1) ;
	println!("random number {:?}", random_num) ;

}
```

1. `rand::thread_rng()` - Tworzy generator liczb losowych, który jest lokalny dla bieżącego wątku. Jest to inicjalizacja generatora losowego.
    
2. `.gen_range(1..6+1)` - Wywołuje metodę `gen_range` na obiekcie generatora losowego. Metoda ta generuje losową liczbę z podanego zakresu (włącznie z dolnym limitem, ale wyłączając górny limit).
