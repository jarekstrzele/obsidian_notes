#rust/ownership 

[[_ 0 Rust From Beginner to Expert 2.0]]


# basic
1. Each value has a variable that is its "owner".
2. A value can have only one owner at a time.
3. if the owner goes out of scope, the value is cleaned up.


## memory
### non-volatile
- hard drives/ssd
- slow but abundant
- persist data
### volatile
- RAM/Cache
- Fast and scarce
- during program
- programs memory layout
	- **stack**:
		- deals with data which has a fixed known size at compile time,
		- the values are stored in order using the last in first out strategy (LIFO)
		- very fast
	- **heap**:
		- deals with data which is of unknown size at compile time
		- data are stored all over the place where a suitable fit for the data
		- slow, require a lot of memory management during program execution
	- **static** — it is used to:
		- store programs,
		- binary instructions
		- static variables
		- clean up of values from it is automatic


>[!info] important
> - primitives such as integer, floats, bools, chars
> - are entirely stored on stack with no reference to heap, and they are copied and not moved by default



# move ownership to a function

```rust
fn main() {
  
   let vec1: Vec<i32> = vec![1,2,3] ;
   takes_ownership(vec1) ;
   // println!("vec 1: {:?}", vec1); //
    
    let vec2: Vec<i32> = vec![1,2,3] ;
    takes_ownership(vec2.clone()) ;
    println!("vec 2: {:?}", vec2) ;
}

fn takes_ownership(v: Vec<i32>){
    println!("vec in function: {:?}", v) ;
}
```









