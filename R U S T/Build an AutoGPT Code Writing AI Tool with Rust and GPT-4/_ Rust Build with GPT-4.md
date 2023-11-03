#udemy  #mcdonogh_shaun

---
#### ==everything by default in Rust is immutable==
```rust
let x : i32 = 10; //is immutable
let mut y : u32 = 20 ; // is mutable
```


---
`rustup` it is how we can manage our rust installation and tooling 

>[!info] CARGO
>It is an immensely powerful package manager in Rust

# First project

## create a project
### `cargo new playground`
cd playground

to add new dependecies (e.g. Tokyo)
cargo add Tokyo
`cargo add tokio`
or full version
`cargo add tokio --features full`

## run the project
`cargo build` , and next `cargo run`
but now you can write only `cargo run` (and `run` will execute `build` command)

or 
`cargo build --release`
domyślnie jest tryb `debug`, teraz aplikacja będzie skompilowana pod kątem wydajnościowym zalezanym w wersji końcowej projektu


## `cargo fmt` fomarts the code



# Function
```rust
fn add_five(num: u32) -> u32{

    num+5

}

  

fn main() {

    println!("add_five to 10 = {:}", add_five(10));

}
```


# Unit test
It is useful for testing functions that ate write on their own pages and therefore then bringing them into (execute on my main page or on some that page that I create )









