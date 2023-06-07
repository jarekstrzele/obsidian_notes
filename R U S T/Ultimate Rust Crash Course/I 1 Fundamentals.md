[[_ Ultimate Rust Crash Course]]

**Rust** is a systems programming language:
- safety
- concurrency
- speed
- from 2006 Graydon Hoare (Mozilla from 2009), version 1.0 in 2015

##### this course: github: ultimate_rust_crash_course
https://github.com/CleanCut/ultimate_rust_crash_course

--------
[[#Cargo]]
[[#variable]]
[[#Scope]]
[[#Memory safety]]
[[#Functions]]
[[#Module]]



---
# Cargo
**cargo** 
- package manager
- build system
- test runner
- documentation generator

#### `cargo new hello_world`
- semantic version (e.g. 0.1.0)

#### `cargo run`
`target/debug/hello`  (executable file of your project, so you can run it directly)
##### `cargo run --release` to compile without debug symbols
(the file will be in `target/release` sub-folder)


------
# variable
- statements are terminated by semicolons
- mimic syntax from other languages
```rust
let bunnies: i32 = 4 ;
let (bunnies, carrots) = (8,  50) ;

```
- variable are immutable by default because:
	- safety  - a lot of bugs never happen if  values never change
	- concurrency - data that never changes can be shared between multiple threads
	- speed - compiler can do extra optimizations on data it knows won't change
```rust
let bunnis = 4 ;
bunnis = 5 ; // error!!! cannot assign twice to immutable variable

```

```rust
let mut bunnis = 4 ;
bunnis = 5 ;
```

#### `const`
- use `const` keyword
- use screaming-snake-case for constants `const WRAP_FACTOR = ask_scotty();`
- type annotation is require `const WRAP_FACTOR: f64 = ask_scotty() ;`
- value must be **constant expression**

1. `const` can be in a global scope
2.  `const` are inlined at compile time - so they are really fast

--------
# Scope
#rust/scope
- Variables have a scope, which is the place in the code that you are allowed to use them.
- it begins where a variable is created and extends to the end of the block
	- *block* - it is  a collection of statements inside **curly braces**
```rust
fn main() {//start scope
	let x = 5;
	{ // a new scope
		let y = 99 ;
	} //end of that new nested scope
	println!("{}", y) ; //GENERATE an error, because y is not defined


} //end of the scope
```
==Values are always immediately dropped when they go out of scope==

**shadowing**
The variables are always local to their scope
```rust
fn main(){
	let x = 10;
	{
		let x = 20; 
	}
	println!("{x}") ; //10

	let meme = "more cowbell" ;
	let meme = make_image(meme);


}


```

------
# Memory safety
#rust/memory 
safety at **compile time**

```rust
fn main(){
	let enigma: i32 ;
	println!("{}", enigma) ; // ERROR, because enigma is declared but not initialized to a value before we try to use is
// it won't compile 
}

```


```rust
fn main(){
	let enigma: i32 ;
	if true {
		enigma = 43;
	} else {
		enigma = 7 ;
	}
	
	println!("{}", enigma) ; // it works, because the compiler can tell that enigma is GUARANTEED to be initilized bedore it is used
}

```


-------
# Functions
#rust/function 
**Functions don't have to appear in the file before code that calls them**
```rust
fn main(){
	do_stuff(); //it workd
}

fn do_stuff(){

}
```

**function parameters are always defined with `name:type`** 
and a return type by `->`
```rust
fn do_stuff(qty: f64, oz: f64) -> f64 {
	//without `return` -- TAIL Expression
	qty*oz
}

```
#### `{ return true; }` is the same as `{ true }`

----
# Module
#rust/module 
```rust
// Silence some warnings so they don't distract from the exercise.
#![allow(unused_variables)]
```


Project structure:
```rust
hello
	- Cargo.toml
	- src
		- lib.rs (this will be added)
		- main.rs
```

`main.rs` is a special file that will be the hello binary  lib.rs
**all items in a library are PRIVATE** event to binaries in the same project

### `use`
it brings an item from some path into some scope 
main.rs (`tests` is the name of project (as `hello`))
#### `use <project_name>::{pub_func, pub_func...} ;`
```rust
use tests::greet ;

fn main(){
	greet() ;
}
```

src/lib.rs
```rust
pub fn greet(){
	println!("Hi") ;
}
```



