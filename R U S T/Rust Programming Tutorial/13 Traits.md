#rust/traits
[[_ Rust Programming Tutorial]]

> [!info]  trait
>It is like a interface in other languages

By implementing the `ToString` trait for your `Person` struct, you are essentially saying that any `Person` object can be converted to a string using the `to_string` method. This means that you can use the `to_string` method on any `Person` object, regardless of where it comes from or how it was created. It also means that other code that expects a `ToString` object can also accept a `Person` object as input.

```rust
struct Person {
  name: String,
  age: u8
}

// ToString is a trait
impl ToString for Person {

  fn to_string(&self) -> String{
    return format!("My name is {}  and I am {}.", self.name, self.age) ;
    
  }
}

fn main(){

  let dom = Person {name: String::from("Jan"), age: 22} ;
  println!("{} ", dom.to_string())
  
}
```





