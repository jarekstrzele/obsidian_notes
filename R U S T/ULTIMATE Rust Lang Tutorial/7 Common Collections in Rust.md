[[_ LetsGetRusty Ultimate Rust Lang Tutorial]]

COLLECTIONS:
- allow you to store multiple values 
- are allocated on the heap:
	- their size is changeable

# vectors

A vector will be dropped out of the scope
```rust
fn main(){
	let a = [1,2,3];
	let v:Vec<i32> = Vec::new();
	v.push(1);
	v.push(2) ;
	v.push(3) ;
	v.push(4) ;

	{
		let v2 = vec![1,2,3];
	}

	// access to third index
	let third: &i32 = &v[2] ;

	// save access - Option
	match v.get(2){
		Some(third) => println!("the third element is {}", third),
		None => println!("THere is no third element."),
	}

}
```






# strings






# hashmaps













