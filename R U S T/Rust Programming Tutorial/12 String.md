#rust/string 
https://www.youtube.com/watch?v=ABYdoxzNJJ8
[[_ Rust Programming Tutorial]]


--------------
# String

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
 cargo run
    Blocking waiting for file lock on build directory
   Compiling my-project v0.1.0 (/home/runner/rustfirst)
    Finished dev [unoptimized + debuginfo] target(s) in 2.32s
     Running `target/debug/my-project`
Length 23
isEmpty? false
My
first
string
in
Rust
Does the string contain 'in'? true
After .push:
 My first string in Rust. This is a new text in the old string. 
 

```


--------
# String Methods




