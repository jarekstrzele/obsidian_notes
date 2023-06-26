#rust/error 
[[_ LetsGetRusty Ultimate Rust Lang Tutorial]]

# `panic!`
>[!info] `panic!`
it will immediately quit your program and print out an error message
```rust
fn main() {
	panic!("crash and burn") ;
}
```


# `Result<T, E>`
definition
```rust
enum Result<T,E> {
	Ok(T),
	Err(E),
}
```
`Option` represents some value or no value

`Result` represents success or failure

e x a m p l e
```rust
use std::fs::File ;

fn main(){
	let f: Result<File, Error> = File::open("hello.txt") ;

	let f: File = match f {
		Ok(file: File) => file ,
		Err(error: Error) => panic!("Problem opening the file: {:?}", error)
	}
}
```


```rust
use std::fs::File ;
use std::io::ErrorKind ;

fn main(){
  let f = File::open("hello.txt") ;

  let f: File = match f {
    Ok(file) => file,
    Err(error) => match error.kind() {
      ErrorKind::NotFound => match File::create("hello.txt") {
        Ok(fc) => fc ,
        Err(e) => panic!("Problem creating the file: {:?}" , e),
      },
      other_error => {
        panic!("Problem opening the file: {:?}", other_error)
      }
    }
  } ; 
}
```


```rust
use std::fs::File;

fn main(){
// instead of :
// let f = match f {
//	Ok(file) => file,
//	Err(error) => panic!("Problem opening the file: ", error).
//}

//unwrap() - returns Ok() or Err()
// expect() - allows to specify the error message that gets passed to the panic macto
	let f = File::open("hello.txt).unwrap() ;
//let f = File::open("jelo.txt").expect("Fail to open hello.txt")
}
```


----
## error propagation
- you have a function whose implementation calls something that could fail 
- you want to return that error back to the caller instead of handling it within the function
- that way gives the caller more control, that caller will decide what to do with that error -- this is called ==error propagation==

#rust/error_propagation

















