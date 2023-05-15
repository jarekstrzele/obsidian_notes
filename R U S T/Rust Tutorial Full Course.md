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
`const ONE_MIL = 1_000_000 ;`








