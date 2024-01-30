#rust  #udemy  #catalin_stefan

--------





-----


>[!info] Rust
>- systems programming (like C, C++)
>- memory safety
>- performance
>- strongly typed


- rust
- intelliJ
	- `plugins > Marketplace> Rust`

# Cargo

>[!info] Cargo
>- it is the package manager for Rust
>- `cargo new <projectName>` 
>- `cargo build` compiles our code into machine runnable code (in the `src` folder)
>- `cargo run`  (build + run code)
>- `cargo clean`
>- `cargo check`  ? errors, ...
>- `cargo doc` generates documentation of the project



# user input
Rust is not a language to user interaction!!!

import library
`use std::io;`

```rust
use std::io ;
 

fn main() {

   //input will be mutable	
   //String::new() create a String object
   let mut input: String = String::new() ;

   // macro	
   println!("say something") ;

   //we are receiving the read_line from the standard library
   // $mut - mutable reference
   match io::stdin().read_line(&mut input){

    Ok(_) => {

        println!("You say {}", input)
    },

    Err(e) => {
        println!("Something went wrond {}", e)
    }
   }
}
```


# comments
```rust
// a line comment

/*
mutliline comment
*/

/// doc comment

//! to document crates

//! # main heading 
```








