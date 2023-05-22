#rust/hashmap 

### `std::collections::HashMap ;`


```rust
  
  

fn main() {

let mut marks = HashMap::new() ;

  

// add value - insert (key, value)

marks.insert("Rust programming", 96) ;

marks.insert("Web Development", 94) ;

marks.insert("UX Design", 75) ;

marks.insert("Professional Computing Studies", 45) ;

  

//length of the hashmap

println!("How many subjects have you studied? {}", marks.len()) ;

  

//get a single value

match marks.get("Web Development") {

Some(mark) => println!("you got {} for Web Dev", mark),

None => println!("You didn't study Web Dev"),

}

  

//remove item

marks.remove("UX Design") ;

  

println!("marks: {:?}", &marks) ;

//loop through HashMap

for (key, value) in &marks {

println!("For {} you get {}%!", key, value)

}

  

println!("Did you study C++? {}", marks.contains_key("C++ programming")) ;

}
```






