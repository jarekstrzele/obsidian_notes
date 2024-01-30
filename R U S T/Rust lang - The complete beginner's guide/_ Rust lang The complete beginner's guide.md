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


//! '''
//! fn main()
//! ''' 

```

`cargo doc` - it will generate a documentation in `target>doc>comment>index.html`


# Printing value

```rust
println!("HEllo, world!");

// formating
println!("My name id {}  snf I'm {} years old", "Alex", 29);

//expressions
println!("a+b={}", 4+5);

//positional arguments
println!("{0} position {2}  position {0} and {1}", "Alex_0", "cat_1", "dog_2");

//named arguments
println!("{name}, {surname}", surname="Smith", name="Alex");

// printing traits
println!("binary: {:b}, hex: {:x}, octal: {:o}" , 5, 5, 5);

//debug - we can't print complex structures
println!("Array {:?}", [1,2,3]);

```



