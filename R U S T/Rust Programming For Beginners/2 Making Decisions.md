#rust 
[[_ Rust Programming for Beginners]]

```rust
fn main(){

  let my_bool = true ;
  // if my_bool == true{}
  if my_bool{
    println!("hello") ;
    
  } else {
    println!("SOmthing wrong")
  }
}

// hello
```

---
# expression `match`
#rust/match 
```rust
fn main(){

  let my_bool = false ;
  match my_bool {
    true => println!("This is true") //this is expression so it ends with `.` not `;`
    , false => println!("This is false")
    ,
  }
}
```



```rust

fn main(){

  let my_bool = 2 ;
  match my_bool {
    1 => println!("This is 1") //this is expression so it ends with `.` not `;`
    , 2 => println!("This is 2")
    , _ => println!("This is something else")
  }
}
```




