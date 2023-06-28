https://www.youtube.com/watch?v=juIINGuZyBc&list=PLai5B987bZ9CoVR-QEIN9foz4QCJ0H2Y8&index=12

#rust/lifetimes
[[_ LetsGetRusty Ultimate Rust Lang Tutorial]]

-------
>[!info] lifetime of a variable
>a variable lives  inside its scope



>[!info] dangling reference
>It is a reference that points to invalid data 
>

example
```rust
fn main() {
	let r: &i32;

	{
		let x: i32 = 5;
		r = &x;
	}

	println!("r: {}", r) ; // generates an error
}
```
`x` - its lifetime ends with its scope so `r` will have a dandling reference


>[!inf] generic lifetime annotations
>- They describe the relationship between the lifetimes of multiple references and how they relate to each other so they don't change the lifetime of  a reference but rather just explain the relationship between different lifetimes 
>- they always start with `'`
>- you can name it like you want `'a` , `'apple` but convention is to start with `'a`  and following the alphabet
>- example:
>	- `&i32` - a reference
>	- `&'a i32` - a reference with an explicit lifetime 
>	- `&'a mut i32` - a mutable reference with an explicit lifetime



`as_str()` - konwertuje wartość `String` ma `&str` (reprezentuje pożyczony *borrowed* napis *slice*)

this code generate an error `error[E0106]: missing lifetime specifier`
```rust
fn main(){
  let string1 = String::from("abcd") ;
  let string2 = String::from("abcd") ;

  let result: &str = longest(string1.as_str(), string2.as_str()) ;
    println!("the longest string is {}", result)  ;

}

fn longest(x: &str, y: &str) -> &str {
  if x.len() > y.len() {
    x
  } else {
    y
  }
}
```


this code i correct with generic annotation of lifetime
```rust
fn main(){
  let string1 = String::from("abcd") ;
  let string2 = String::from("abcd") ;

  let result: &str = longest(string1.as_str(), string2.as_str()) ;
  println!("the longest string is {}", result)  ;
  
  
}

// generic lifetime annotation
// lifetime of return value will be the same as the lifetime of arguments
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
  if x.len() > y.len() {
    x
  } else {
    y
  }
}
```


----
## `struct` with lifetime annotations
```rust

struct ImportantExcept<'a> {
  part: &'a str,
}

fn main(){
  let novel =String::from("Call me Ishmael. SOme years ") ;
  let first_sentence: &str = novel.split('.').next().expect("Could not found.") ;
  let i = ImportantExcept{
    part: first_sentence,
  } ;
  
}
```


---
## lifetime illusion RULES
*input lifetime* - arguments being passed in a function 

*output lifetime* - it is a lifetime of the return values

>![info] rules
>1. each parameter that is a reference gets its own lifetime parameter
>2. if there is exactly one input lifetime parameter, that lifetime is assigned to all output lifetime parameters
>3. 











