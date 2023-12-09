#rust/hashmap 

- collection that stores data as key-value pairs
	- data is located using the "key"
	- the data is the "value"
- similar to definitions in a dictionary
- very fast to retrieve data using the key
- data are stored in ==random order ==

```rust
let mut people = Hashmap::new();
people.insert("Susan", 21) ; //insert(key, value)
people.insert("Ed", 13) ;
people.insert("Will", 14) ;
people.insert("Cathy", 22) ;
people.remove("Susan") ; //remove(key)

match people.get("Ed") {
	Some(age) => println!("Age = {:?}", age),
	None => println!("nt found"),
}

for (person, age) in people.iter() {
	println!("person = {:?}, age = {:?}", person, age) ;
}

for person in people.keys(){
//.....
}

for age in people.values(){
//.........
}

```


```rust
use std::collections::HashMap ;

#[derive(Debug)]
struct Contents {
	content: String,
}

fn main(){
	let mut lockers = HashMap::new();
	lockers.insert(1, Contents {content: "stuff_1".to_owned()}) ;
	lockers.insert(2, Contents {content: "stuff_2".to_owned()}) ;
	lockers.insert(3, Contents {content: "stuff_3".to_owned()}) ;

	for (locker_num, content) in lockers.iter(){
		println!("key = {:?} , value = {:?}", locker_num, content)
	}
}
```







