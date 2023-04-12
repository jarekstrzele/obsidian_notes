
# A simple Hello World

In the editor:
- make `main.rs` file
- **inside the file you must declare `main` function, because all Rust programs begin with the main function**
```rust
fn main(){
	println!("Hello world") ;
}
```
in the terminal:
- `rustc main.rs`
- `./main` or `main`  or `main.exe`


# The Hello World App with `cargo`
#rust/cargo 

### `cargo new projectName`

`cargo new hello-world-cargo`
`cargo new hello-world-cargo --bin`

>  `cargo new myApp` creates a Rust project that builds a library, while `cargo new myApp --bin` creates a Rust project that builds an executable binary.

Inside the project folder
### `cargo run`