#rust #udemy  #azam_nouman

- `rustc --version`
- `cargo --version`
- `rustup update`


## https://play.rust-lang.org/?version=stable&mode=debug&edition=2021


# one file
VS CODE:
- `rustc fileName.rs` ->
- `./fileName` to execute the program

settings in VS Code
- format on save
- Mouse Wheel Zoom

# project
- `cargo new projectName`
- `cargo run` (in `target`>`debug` will be created a executing file)



----------
# Variable and Constants
variables are immutable by default

```rust
fn main() {
    let x: i16 = 1221;
    println!("x = {x}");
    // x = 22; // error
    
    let mut y = 21; // mutable y
    y=100;
    println!("y={y}");
}
```

---
# Primitive Data Types
`char` , `bool`, `u32`, `i32`  































