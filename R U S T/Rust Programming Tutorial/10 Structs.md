#rust/struct
[[_ Rust Programming Tutorial]]

----
[[#Structs]]
[[#Struct Tuples]]
[[#Imp]]



------
# Structs

>[!info] `struct`
>It is a way you can group similar  bits of information into one sort  of central data type

```rust
struct Color{
  red: u8,
  green: u8,
  blue: u8
}


fn main(){
  let bg = Color {red: 255, green: 70, blue: 15} ;

  // bg.blue = 45 ; //error, you can't change the value
  println!("{}  {}  {}", bg.red, bg.green, bg.blue) ;
  
}
output: 255  70  15
```

to change the value of attr:
```rust
struct Color{
  red: u8,
  green: u8,
  blue: u8
}


fn main(){
  let mut bg = Color {red: 255, green: 70, blue: 15} ;

  bg.red = 45 ;
  println!("{}  {}  {}", bg.red, bg.green, bg.blue) ;
  
}
output:
45  70  15
```

---
# Struct Tuples
```rust
struct Color(u8, u8, u8) ;

fn main(){
  let mut red = Color(255,0,0) ;
  red.2 = 45 ;
  println!("{}  {}  {}", red.0, red.1, red.2) ;
  
}
output
255  0  45
```



------------
# `Imp`
key word that allows us implements methods 
```rust
struct Rectangle {
  width: u32,
  height: u32
}

impl Rectangle {

  fn print_desc(&self){
    
    println!("rect {} x {} ", self.width, self.height ) ;
  }

  fn is_square(&self) -> bool{
    self.width == self.height 
  }
}

fn main(){
  let my_rect = Rectangle{width:10, height:20} ;

  my_rect.print_desc();

  println!("Is Rectangle? {}", my_rect.is_square()) ;
   

  
}
```

#rust/borrowing
In Rust, borrowing refers to the mechanism used to manage ownership and access to memory. When a variable or object is borrowed, it means that another piece of code is given temporary access to it, but without taking ownership of it.

There are two types of borrowing in Rust: mutable borrowing (`&mut`) and immutable borrowing (`&`).

Mutable borrowing (`&mut`) allows the borrowing code to modify the borrowed variable or object. However, only one mutable borrow is allowed at a time for a given object, and the borrowing code must return ownership of the object before any other code can access it.

Immutable borrowing (`&`) allows the borrowing code to read the borrowed variable or object, but not modify it. Multiple immutable borrows can exist for a given object at the same time, but no mutable borrows are allowed while any immutable borrows are still active.

Borrowing in Rust helps prevent common issues like data races and memory leaks, while still allowing efficient and flexible memory management.

#rust/ownershipt
Ownership is a unique feature of Rust that helps ensure memory safety and prevents issues like data races and null pointer dereferencing. In Rust, every value has an owner, which is a variable or binding that holds the value. When an owner goes out of scope, Rust automatically calls the `drop` function to release the memory used by the value.

There are three key rules that govern ownership in Rust:

1.  Each value in Rust has a single owner at any given time.
2.  When the owner goes out of scope, the value is dropped and the memory is freed.
3.  Ownership can be transferred between variables using the `move` keyword or borrowed using references (`&` and `&mut`).

By enforcing these rules, Rust eliminates common issues like use-after-free errors and dangling pointers. Additionally, Rust's ownership model enables safe and efficient memory management without requiring a garbage collector.








