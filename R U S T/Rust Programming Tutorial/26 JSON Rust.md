#rust/json
[[_ Rust Programming Tutorial]]

```toml
[dependencies]

serde = "1.0.163"

serde_json = "1.0.96"

serde_derive = "1.0.163"
```


## First way
```rust
  

use serde_json ;

use serde_json::Value as JsonValue;

  

fn main() {

let json_str = r#"

{

"name":"Domenic",

"age":65,

"is_male":true

}

"#;

  

// res is a Result type

let res = serde_json::from_str(json_str);

  

if res.is_ok(){

let p: JsonValue = res.unwrap() ;

println!("The name is {}", p["name"]) ;

	println!("The name is {}", p["name"].as_str().unwrap()) ;
	} else {
	println!("Sorry! Could not parse JSON: :(") ;
	}
}

output
The name is "Domenic"
The name is Domenic
```

## Second way
```rust
  

use serde_json ;

use serde_json::Value as JsonValue;

use serde ;

use serde_derive::{Serialize, Deserialize};

  
  

#[derive(Serialize, Deserialize)]

struct Person {

name: String,

age: u8,

is_male: bool,

}

  
  
  

fn main() {

let json_str = r#"

{

"name":"Domenic",

"age":65,

"is_male":true

}

"#;

  

// res is a Result type

let res: Result<Person, serde_json::Error> = serde_json::from_str(json_str);

  

if res.is_ok(){

let p: Person = res.unwrap() ;

println!("The name is {}",p.name) ;

println!("The age is {}",p.age) ;

println!("The is_male is {}",p.is_male) ;

  

} else {

println!("Sorry! Could not parse JSON: :(") ;

}

  

}

output
The name is Domenic
The age is 65
The is_male is true

```









