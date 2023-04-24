#rust 
read the input from console and ouput some answers

CONCEPT:
- functions
- basic data types
- standard library
- memory ownership

----
# Basic data types
- booleans
- characters
- integers
- floats

## integers
`u` unsigned integer POSITIVE only
`i` signed integer
`u8, i8` $0$ (one bite)
`u16, i16` $00$
`u32, i32` $0000$
`u64, i64` $00000000$
`u128, i128` $0000000000000000$

`usize` or `isize`  architecture dependent types 

## float
`f32`
`f64`

## boolean
`bool` $0$

# char
`char` $0000$

----------
# Function
`cargo new mars_calc`
`cd mars_calc`
`cargo run`

#### `fn main`
it is always the first code that runs - the entry point

==use snack_case_convention== to name functions

>[!important] `return`
>The last expression in every function that doesn't have a semicolon at the end  is AUTOMATICALLY returned


```rust
fn main() {
    println!("Hello, world!");
    calculagte_weight_on_mars(100.0) ;
}

fn calculagte_weight_on_mars(weight: f32) -> f32{
    50.0
}
```


--------
# Macro
>[!info] macro  `!`
>- macros are used for metaprogramming
>- this is a way of writing code that writes more code
>- can be call with  variable numbers of parameters and with different types
>- its definitions is more complex than function one
>- 
>

`println!("abc")` 
`println!("somthing {}", x)`
`printlm!("NUmber: {}, String: {}", 100, "abc")`

#### `cargo-expand`
it is on github 
`cargo install cargo-expand`

write in the terminal:
`cargo expand` -> this will show us what all of the mactos in our code are expanded into

```rust
fn main() {
    println!("Weight on Mars: {}kg", calculagte_weight_on_mars(87.0)) ;
}

fn calculagte_weight_on_mars(weight: f32) -> f32{
    (weight/9.81) * 3.711
}
```

----
# Mutability

==all variables in Rust are IMMUTABLE by default==
` x = x+3 ;` -> error
```rust
let mars_weight = calculagte_weight_on_mars(100.0) ;
 mars_weight = mars_weight * 1000.0 ;

mars_weight = mars_weight * 1000.0 ;
  |     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ cannot assign twice to immutable variable
```
`mut` change variables to mutable one

```rust
 let mut mars_weight = calculagte_weight_on_mars(100.0) ;
 mars_weight = mars_weight * 1000.0 ;
```
it is OK

--------
# Standard Library
```rust
use std::io ;

fn main() {

	// String is  Struct
    let mut input = String::new() ;
    io::stdin().read_line(&mut input) ;

    let mut mars_weight = calculagte_weight_on_mars(100.0) ;
    mars_weight = mars_weight * 1000.0 ;
    println!("Weight on Mars: {}kg", mars_weight) ;
}

fn calculagte_weight_on_mars(weight: f32) -> f32{
    (weight/9.81) * 3.711
}
```

----
# OWNERSHIP

There are three ownership rules in Rust:
==1. Each value in Rust is owned by a variable.==
in the function body there is :
```rust
let mut input == String::new() ;
io::stdin().read_line(&mut input) ;
```
the string is owned by `input` variable


==2. When the owner goes out of scope, the value will be deallocated==
When the function exits, the drop function on the string will be invoked automatically by the compile

==3. There can only be ONE owner at a time.==
```rust
let mut input == String::new() ;
let mut s = input ;
io::stdin().read_line(&mut input) ;
```
this code generates an error, because you use `input` as a parameter of `read_line` function, but you transfered the ownership of the string to the variable `s`

The string exists on the heap. When you will do the same with the numebr (it exists on the stack), the value will be copy to a new variable.
```rust
let a = 5;
let b = a; // the 5 will be copied to the b

```
this code won't generate an error

A PROBLEM: when you pass a variable to the function as a argument, you transfer the ownership, so
this code generate an error:
```rust
fn main() {
	let mut input == String::new() ;
	some_fn(input) ; //this line transfer the ownership of the string from `input` to the function `some_fn`
	let mut s = input ;
	io::stdin().read_line(&mut input) ;
}

fn some_fn(s: String){} ; // `s` will be the owner of the String
```


------
# References and Borrowing
```rust
fn main() {
	let mut input == String::new() ;
	some_fn(&input) ; // Now you pass the reference not the value
	let mut s = input ;
	io::stdin().read_line(&mut input) ;
}

// Now the function expects a reference
// the function just borrows the string
fn some_fn(s: &String){} ; // `s` is not the owner of the String
```

>[!inportent] Borrowing
>Passing references as parameters


## **references** are immutable by default
```rust
fn some_fn(s: &String){
	s.push_str("a") ; // it generates an error because the s is a immutable by default
} ; 
```

## mutable **references**
```rust
fn main() {
	let mut input == String::new() ;
	some_fn(&mut input) ; // mutable reference
	let mut s = input ;
	io::stdin().read_line(&mut input) ;
}

// mutable reference
fn some_fn(s: &mut String){
	s.push_str("a") ; 
} ; // `
```


## restrictions 
this code is correct (two variables with the same immutable reference)
```rust
fn main() {

println!("Write your weight on Earth: ") ;

let mut input = String::new() ;

let s1 = &input ;
let s2 = &input;
println!("{} {} ", s1, s2) ;
}
```

this code generates an error:
```rust
fn main() {

println!("Write your weight on Earth: ") ;

let mut input = String::new() ;
	let s1 = &input ;
	let mut s2 = &mut input; //mutable

println!("{} {} ", s1, s2) ;

println!("Ok") ;
```


ok code
```rust
fn main() {

println!("Write your weight on Earth: ") ;

let mut input = String::new() ;

io::stdin().read_line(&mut input) ;

  

borrow_string(&input) ;

own_string(input)

}

  

fn borrow_string(s: &String){

println!("{}", s) ;

}

  

fn own_string(s: String){

println!("{}", s) ;

}
```
