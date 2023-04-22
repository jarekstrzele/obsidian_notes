#rust/string 
https://www.youtube.com/watch?v=ABYdoxzNJJ8

```rust
fn main(){
 let mut my_string = String::from("My first string in Rust") ;

  println!("Length {}", my_string.len()) ;
  println!("isEmpty? {}", my_string.is_empty()) ;
   
  for token in my_string.split_whitespace(){
    println!("{}", token) ;
  }

  println!("Does the string contain 'in'? {}", my_string.contains("in"));

  my_string.push_str(". This is a new text in the old string.") ;
  println!("After .push:\n {} ", my_string) ;
}

output

```






