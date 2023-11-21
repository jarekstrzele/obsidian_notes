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

```rust
    let mut chars: Vec<char> = Vec::new();
    chars.insert(0, 'h') ;
    chars.insert(1, 'e') ;
    chars.insert(2, 'l') ;
    chars.push('l') ;
    chars.push('o') ;
    println!("chars: {:?}", chars) ; //chars: ['h', 'e', 'l', 'l', 'o']
    chars.iter().for_each(|c: &char| print!("{}", c)) ; //hello
```

```rust
    let chars_again: Vec<char> = vec!('h','e','l','l','o') ;
    dbg!(&chars_again) ;
//     [src/main.rs:6] &chars_again = [
//     'h',
//     'e',
//     'l',
//     'l',
//     'o',
// ]
    
```


```rust
  let chars_again: Vec<char> = vec!('h','e','l','l','o') ;
  
    let collected: String = chars_again.iter().collect();
    // dbg!(collected) ; /[src/main.rs:8] collected = "hello"
    
```


```rust
fn main() {

    let chars_again: Vec<char> = vec!('h','e','l','l','o') ;
  
    for c in chars_again{
        print!("{}", c) ;
        if c=='o' {
            print!(" world!") ;
        }
        
    }
}
```


# Closure
#rust/clone 

```rust
fn main() {

    let num : i32 = 5;
    let add_num = |x: i32| x + num ;
    let new_num: i32 = add_num(7) ;
    dbg!(new_num) ;
}
```


# Number Literals and Raw Strings

```rust
fn main() {

    //Number Literals
    println!("Big Number is {}", 98_222_000) ; //     Big Number is 98222000
    println!("Hex is {}", 0x77) ;// Hex is 119
    println!("Octal is {}", 0o77) ;// Octal is 63
    println!("Binary is {}", 0b111_000) ; // Binary is 56
    println!("Bytes 'A' is {}", b'A') ; // Bytes 'A' is 65

    //raw string literal
    let text: &str = r#""message": "Rust is Awesome "#;
    dbg!(text); //[src/main.rs:14] text = "\\\"message\": \"Rust is Awesome "
        
    
}

```


# Working Low Level with Binary
```rust
fn main() {
    let a: u8 = 0b_1010_1010;
    let b: u8 = 0b_1001_1010;
    println!("'a' value is {}" , a); // 'a' value is 170
    println!("'b' value is {}" , b); //'b' value is 154
  
    println!("a in binary {:08b}", a); // a in binary 10101010
    println!("b in binary {:08b}", b); // b in binary 10011010

    
    // logic gates
    println!("AND: {:08b}", a & b) ; // AND: 10001010
    println!("OR: {:08b}", a | b) ;// OR: 10111010
    println!("xOR: {:08b}", a ^ b) ;// xOR: 00110000
    println!("NOT: {:08b}", !a) ;// NOT: 01010101
    
    // bitwise operators
    println!("a = {:08b}", a) ;  //   a =    10101010
    println!("a << 1 {:08b}", a<<1);//a << 1 01010100
    println!("a << 1 {:08b}", a>>1);//a << 1 01010101 
}
```




# Rust std Library
#rust/std
### `use std::collections::{HashMap, BTreeMap} ;`




