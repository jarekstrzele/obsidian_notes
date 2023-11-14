#rust 

## `cargo new playaround`


```rust
const OUR_COURSE: &str = "Rust with AutoGPT" ;

fn main() {
    println!("Hello, on {OUR_COURSE}!");

    //stack
    let x: i32;
    x = 4;
    println!("x is {x}") ;

    // for loop
    for i in 0..=x{
        if i != 4 {
            println!("{i}" );
        } else {
            println!("{i} it is four");
        }
    }

    let mut z: i32 = 5;
    print!("z was {z}") ;
    z = 10 ;
    print!(" but now is {z}");

    let emoji_char: char = '😂';
    println!("\nmy emoji: {emoji_char}") ;

    // array on stack
    let my_ints: [u32; 5] = [1,2,10,20,3];
    println!("my ints is {my_ints:#?}") ;
    let new_arr = my_ints.map(|a| a*2) ;
    println!("my ints is {new_arr:?}") ;
}
```










