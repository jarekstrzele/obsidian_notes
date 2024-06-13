#rust  

# hello world
```rust
// &'static is a "lifetime specifier", something you'll learn more about later
pub fn hello() -> &'static str {
    "Hello, World!"
}

fn main(){
    println!("{}", hello()) ;
}
```


# reverse string






















