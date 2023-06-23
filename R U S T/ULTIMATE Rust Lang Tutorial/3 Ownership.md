[[_ LetsGetRusty Ultimate Rust Lang Tutorial]]
#rust/ownership 


 _ | PROS | CONS
 ---|---|---
Garbage collection | - error free - faster write time | - no control over memory  - slower and unpredictable runtime performance - larger program size
manual memory management | - control over memory - faster runtime - smaller program size | error prone - slower write time
ownership model|-control over memory - error free - faster runtime - smaller program size | -slower write time . learning curve (fighting with the borrow checker)

![[Rust_stack_heap.excalidraw || 600]]

the pointer to "hello" is on the stack, but "hello" is on the heap

OWNERSHIP RULES
1. Each value in Rust has a variable that's called its owner.
2. there can only be one owner at a time
3. when the owner goes out of scope , the value will be dropped

```rust
fn main(){
	let x:i32 = 5;
	let y: i32 = x ; //copy

	let s1: String = String::from("hello") ;
	let s2: String = s1 ;
}
```

`s1` moves its ownership to `s2`
![[rust_move_ownership.excalidraw | 600]]

to copy `String` use `clone()` method
```rust
let s1 = String::from("hello") ;
let s2 = s1.clone() ;
```

## Copy Traits
integer, booleans, characters implement this trait

```rust
fn main() {
	let s = String::from("hello") ;
	takes_ownership(s) ;
	println!("s = {}", s) ; // generates error `s` was moved to function

	let x: i32 = 5;
	makes_copy(x) ;
	println!("{}", x) ; // it doesn't generate an error, because integer implement Trait Copy, 



	fn takes_ownership(some_string: String){
	println!("{}", some_string) ;
	}


	fn makes_copy(some_integer: i32){
		println!("{}", some_integer) ;
	}
}
```


**give ownership**
```rust
fn main(){
	let s1: String = gives_ownership();
	println!("s1= {}", s1) ;

	fn gives_ownership() -> String {
		let some_string: String = String::from("hello") ;

	some_string
	}
}
```

**take ownership and give it back**
```rust
fn main(){
	let s2 = String::from("hello") ;
	let s3 = takes_and_gives_back(s2) ;

	fn takes_and_gives_back(a_string: String) -> String {
	a_string
	}
}
```

### using string without moving its ownership
```rust
fn main(){
	let s1: String = String::from("hello") ;
	let len: usize = calculate_length(&s1);
	println!("the length of '{}' is {}.", s1, len) ;

	fn calculate_length(s: &String) -> usize
}
```





