#rust/struct

----
[[#Structs]]
[[#Struct Tuples]]



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
ley word that allows us implements methods 






