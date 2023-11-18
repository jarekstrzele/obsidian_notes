#rust 

## `cargo new playaround`

# Fixed size variables
```Rust
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


# Dynamic Sized Variables

```rust


fn main() {
   
    let name: &str = "Shoaun is a lamb" ;
    println!("name is {:?}", name );

    let dynamic_name: String = String::from("Shoan is a lamb") ;
    println!("Dynamic name: {dynamic_name}") ;
    println!("dynamic name in memody {:p}", &dynamic_name) ;
    
    let dynamic_name1: String = name.to_string();
    let dynamic_name2: String = "Shoan".to_string();
    
    let str_slice: &str = &dynamic_name[0..5] ;
    //let println!("str_slice is {:?}", str_slice) ;
    println!("str_slice is {:?}", str_slice);
    
    let mut chars: Vec<char> = Vec::new();
    chars.insert(0, 'h') ;
    chars.insert(1, 'e') ;
    chars.insert(2, 'l') ;
    chars.push('l') ;
    chars.push('o') ;
    println!("chars: {:?}", chars) ;
    //dbg!(chars) ; // dbg borrows chars
    dbg!(&chars) ;
    let removed_char: char = chars.pop().unwrap();
    println!("pop()-> {}", removed_char);

    
}

```

# Basic collection















