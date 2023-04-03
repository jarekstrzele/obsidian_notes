==CRATE==  = package or library
==Module== is inside the crate, a specific piece of functionality, e.g. `IO` module

### `use std::io ;` 
`std` - it is a crate
`io` it is a module input/output
`::` it is the path separator operator , allows to go from package to module, or from the module to specific function

```rust
use std::io;

fn main(){
    println!("Hello world!") ;
   let mut input = String::new(); //new() a String object
   
   //stdin - standard input=terminal
   //&mut input - mutable reference to this input
   // variable
   //so read_line can directly modify the data
   // that's stored inside the input variable
   io::stdin().read_line(&mut input).expect("failed to read line") ; 
   //read_line(input) => the function read_line will
   // copy the value of input
   // this behaviour is default
   //(&input) - this give a reference but it is immutable
   //($mut input)
   println!("{}", input) ;

}
```






