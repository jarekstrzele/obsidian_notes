[[_ LetsGetRusty Ultimate Rust Lang Tutorial]]

COLLECTIONS:
- allow you to store multiple values 
- are allocated on the heap:
	- their size is changeable

-------
[[#vectors]]
[[#strings]]
[[#hashmaps]]



----





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

```rust
fn main(){
  let mut v = vec![10,20,30,40,50] ;

  let third = &v[2] ;
  v.push(6);
  println!("the third element is {}", third) ;
}
```
this code generates an error:
```bsh
let third = &v[2] ;
  |            - immutable borrow occurs here
6 |   v.push(6);
  |   ^^^^^^^^^ mutable borrow occurs here
```
W tym kodzie zastosowano referencję (`&`) przy przypisaniu wartości trzeciego elementu wektora do zmiennej "third".

Jednak następnie dodano nowy element o wartości 6 do wektora za pomocą metody "push". Operacja ta może spowodować realokację wektora, jeśli przekroczy jego pojemność. W rezultacie, referencja "third" może wskazywać na niepoprawną lokalizację pamięci, co prowadzi do niezdefiniowanego zachowania.

```rust
fn main(){
  let mut v = vec![10,20,30,40,50] ;

 for i in &mut v {
   *i *= 11 ;
   println!("{}", i) ;
 }
}
```


The vector can contain only one type of elements.
If you want to store different types in one vector:
```rust

fn main(){
  enum SpreadsheetCell{
    Int(i32),
    Float(f64),
    Text(String),
  }

  let row = vec![
    SpreadsheetCell::Int(3),
    SpreadsheetCell::Text(String::from("blue")),
    SpreadsheetCell::Float(10.12),
  ] ;

  match row[0] {
    SpreadsheetCell::Int(i) => println!("{}", i),
    _ => println!("Not integer!")
  }
}


```


-----------------
# strings
Strings are stored as a collection of UTF-8 encoded bytes
```rust
let s1: String = String::new();
let s2: &str = "initial contents" ;
let s3: String = s2.to_string();
let s4: String = String::from("initial content") ;
```

adding characters to String:
`push()` add one character to the end of the string 
`push_str()` add a string slice to the end of the string

```rust
fn main(){
  let mut s = String::from("foo") ;
  s.push_str("bar") ;
  s.push('!') ;
  println!("{s}") ;
}
// output 
foobar!
```

```rust
fn main(){
  let s1 = String::from("hello, ") ;
  let s2 = String::from("world!") ;
  //concatanation
  let s3 = format!("{}{}", s1, s2) ;
  println!("{s3}") ;
  
}
```

the type `String` can be indexing `s1[0]`

```rust
fn main(){
  let s1 = String::from("hello world") ;
  //let my_h = s1[0] ; // error

  for b in s1.bytes(){
    println!("{b}") ;
  }

  
  for b in s1.chars(){
    println!("{b}") ;
  }
  
}
```




# hashmaps
```rust
use std::collections::HashMap;

fn main(){
	let blue: String = String::from("Blue") ;
	let yellow: String = String::from("Yellow") ;
	let mut scores: HashMap<String, i32> = HashMap::new() ;

	scores.insert(blue, 10) ; //you move the ownership from string to hashmap
	scores.insert(yellow, 50) ;

	let score = scores.get("Blue") ;
  println!("{:?}", score) ; // Some(10)
	for(k, v) in &scores {
	    println!("{} : {}", k, v) ;
	}
  println!("{:?}", scores) ;
}

--- output
Some(10)
Blue : 10
Yellow : 50
{"Blue": 10, "Yellow": 50}
```


```rust
use std::collections::HashMap;

fn main(){
  let text = "hello world wonderful world" ;

  let mut map: HashMap<&str, i32> = HashMap::new() ;
  
  for word in text.split_whitespace() {
    let count = map.entry(word).or_insert(0) ;
    *count += 1 ;
    
  }
  println!("{:?} ", map) ;
  
}

--- output
{"world": 2, "wonderful": 1, "hello": 1} 
```











