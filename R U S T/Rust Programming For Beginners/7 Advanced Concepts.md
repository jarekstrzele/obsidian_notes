[[_ Rust Programming for Beginners]]

---
[[#Drive Macro for printing info]]
[[#Type Annotations]]
[[#Enum]]
[[#Advanced Match]]
[[#Option]]
[[#Documentations]]
[[#Result]]
[[#Hashmap]]





----
# Drive Macro for printing info
#rust/copy  #rust/clone   #rust/derive 

>[!info] Derive
>It is a special macrto that is applied to `enum` and `struct`
>`#[dervie(...)]` 
>`Debug` debug printing functionaity 
>`Clone`
>`Copy`  copies the argument, so ownership is not move from `struct` or `enum`


```rust
#[derive(Debug, Clone, Copy)]
enum Position {
  Manager,
  Supervisor,
  Worker,
}

#[derive(Debug, Clone, Copy)]
struct Employee {
  position: Position,
  work_hours: i64,
}

fn print_emp(emp: Employee) {
  println!("{:?}", emp) ;
}

fn main() {
  let me = Employee {
    position: Position::Worker,
    work_hours: 40,
  };

  println!("{:?}", me) ;
  println!("{:?}", me.position) ;
  print_emp(me);
  print_emp(me);
}
```


#rust/traits 
>In Rust, `Clone` and `Copy` are traits used for creating copies of values, but they have different purposes and behaviors.

> The `Copy` trait is used for types that are trivially copyable, meaning that when a value of that type is assigned to another variable or passed to a function, a bit-for-bit copy of the value is made. This means that the original value is not affected by changes made to the copied value, and the two values can be used independently. Types that implement `Copy` include `bool`, `char`, numeric types (`i32`, `f64`, etc.), and tuples containing types that implement `Copy`.

> On the other hand, the `Clone` trait is used for types that need a deep copy, meaning that a new object with the same data is created. This is typically used for types that own heap-allocated memory, such as `String` and `Vec<T>`. When a value of a type that implements `Clone` is assigned to another variable or passed to a function, a new copy of the value is created, and changes made to the copied value do not affect the original value.

> It's worth noting that not all types can implement both traits - some types cannot be trivially copied, and some cannot be cloned due to ownership and borrowing rules. It's also worth noting that `Copy` and `Clone` are both marker traits, meaning that they don't define any methods themselves, but rather signal to the compiler how the type should be treated.



-------
# Type Annotations
- required for functions signatures
- types are usually inferred
- can also be specified in code (expliciti type annotations)

```rust
// this type annotations  is required
fn print_many (msg: &str, count: i32) {}

// it is optional
let num: i32 = 15 ;
let a: char = 'a' ;
let left_click: Mouse = Mouse::LeftClick ;

```

## generics
```rust
// type annotation is optional
let nums: Vec<i32> = vec![1,2,3] ;
let letters: Vec<char> = vec!['a','b','c'] ;
let clicks: Vec<Mouse> = vec![
	Mouse::LeftClick,
	Mouse::RightClick,
	Mouse::MiddleClick,
	
]
```

------
# Enum
#rust/enum 
[[4 Data#Enum]]

```rust
enum Mouse {
	LeftClick,
	RightClick,
	MiddleClick,
	Scroll(i32),
	Move(i32, i32),
}
```

`Scroll(i32)` and `Move(i32, i32)` - they have  additional data associated with it

```rust
enum PromoDiscount {
	NewUser,
	Holidey(String),
}

enum Discount { 
	 Percent(f64),
	 Flat(i32),
	 Promo(PromoDiscount),
	 Custom(String),
 }
```

==If you have some additional data associated, you have to add them, when you create an instance of `enum`==


-------
# Advanced Match
[[2 Making Decisions#expression `match`]]

## match with `enum`
```rust
enum Discount {
  Percent(i32),
  Flat(i32),
}

fn main() {
  let n = 3 ;
  match n {
    n => println!("three"),
    other => println!("{:?}", other), // _ => ...
  }

  let flat = Discount::Flat(2) ;
  match flat {
    Discount::Flat(2) => println!("flat 2") ,
    Discount::Flat(amount) => println!("flat discount of {:?}", amount) ,
    _ => (), //return nothing
  }
  
}
```


## match with `struct`
```rust
struct Ticket {
  event: String,
  price: i32,
}

fn main() {
  
  let concert = Ticket {
    event: "concert".to_owned() ,
    price: 50,
  } ;

  match concert {
    Ticket {price: 50, event} => println!("event  50 {:?}", event) ,
    Ticket {price, ..} => println!("price {:?}", price) ,
  }
}
```


---
```rust
enum Ticket{
  Backstage(f64, String),
  Standard(f64),
  Vip(f64, String) ,
  
}

fn main() {
  
  let tickets = vec![
   Ticket::Backstage(50.0, "Billy".to_owned()) ,
   Ticket::Standard(15.0) ,
   Ticket::Vip(30.0, "Amy".to_owned()) ,
  ] ;

  for ticket in tickets {
    match ticket {
      Ticket::Backstage(price, holder) => {
        println!("Backstage ticker,  Holder: {:?}, price: {:?}", holder, price)},
      Ticket::Standard(price) => println!("Standard price {:?}", price),
      Ticket::Vip(price, holder) => {
        println!("Vip ticket, Holder: {:?}, price: {:?}", holder, price)
      }
    }
  }
    
  
}
```
cargo run
```rust
Backstage ticker,  Holder: "Billy", price: 50.0
Standard price 15.0
Backstage ticker,  Holder: "Amy", price: 30.0
```


-----
# Option
#rust/option

>[!info] Option
>- a type that may be one of two things
>	- some data of a specified type
>	- Nothing
>- Used in scenarios where data may not be required or is unavailable
>	- unable to find something
>	- ran out of items in a list
>	- form field not filled out
>- It is a part of the Rust library

**Definition**:
```rust
enum Option<T>{
	Some(T),
	None
}
```

**Example**:
```rust
struct Customer {
  age: Option<i32>,
  email: String,
}

fn main(){
  let mark = Customer {
    age: Some(22),
    email: "mark@pp.com".to_owned(),
  };

  let backy = Customer {
    age: Some(11),
    email: "backy@pp.com".to_owned(),
  };

  match backy.age {
    Some(that_age) => println!("customer is {:?} years old", that_age),
    None => println!("customer age not provided"),
  }
}
```

```rust
struct GroceryItem{
	name: String,
	qty: i32,
}

fn find_quantity(name: &str) -> Option<i32> {
	let groceries = vec![
		GroceryItem { name: "bananas".to_owned(), qty:4, },
		GroceryItem { name: "eggs".to_owned(), qty:12, },
		GroceryItem { name: "bread".to_owned(), qty:1, },	
	];

	for item in groceries {
		if item.name == name {
			return Some(item.qty) ;
		}
	}
	None
}
```

```rust
struct Survey {
  q1: Option<i32>,
  q2: Option<bool>,
  q3: Option<String>,
}

fn main(){
  let response = Survey {
    q1: Some(12),
    q2: Some(true),
    q3: Some("A".to_owned()),
  } ;

  match response.q1 {
    Some(ans) => println!("q1: {:?}", ans),
    None => println!("q1: no response"),
  }

  match response.q2 {
    Some(ans) => println!("q1: {:?}", ans),
    None => println!("q1: no response"),
  }

  match response.q3 {
    Some(ans) => println!("q1: {:?}", ans),
    None => println!("q1: no response"),
  }
  
}
```


```rust
struct Student {
  name: String,
  locker: Option<i32>,
}

fn main(){
  let s = Student {
    name: "Peter".to_owned(),
    locker: Some(2),
  };

  let s2 = Student {
    name: "Johm".to_owned(),
    locker: None,
  } ;


  match s.locker {
    Some(num) => println!("{:?} {:?}", num, s.name),
    None => println!("no locker assigned"),
  }

    match s2.locker {
    Some(num) => println!("{:?} {:?}", num, s.name),
    None => println!("no locker assigned"),
  }
  
}
```


---------
# Documentations
#rust/doc 

### `///` genereted documentations

```rust
/// a favorite color
enum Color {
  Red,
  Blue,
}

/// A piece of mail.
struct Main {
  /// The destination address.
  address: String,
}

///adds two numbers together
fn add(a: i32, b: i32) -> i32 {
  a + b 
}

fn main(){
  
}
```

### `cargo doc --open`


## Accessing standard Library Documentation

### `rustup doc`  -> .rust/....

```rust
fn main(){
	/// my list
	let nums = vec![1,2,3] ;
}
```

e.g. file:///home/jarek/.rustup/toolchains/stable-x86_64-unknown-linux-gnu/share/doc/rust/html/std/macro.vec.html

```rust
fn main(){
	/// my list
	let nums = vec![1,2,3] ;
	match nums.is_empty(){
		true => println!("No elements"),
		false => println!("There are some items in vec")
	}
}
```

```rust
fn main(){
	
	let s = "heLLo" ;
	
	println!("{:?}", s.to_uppercase()) ;
	
	println!("{:?}", s.to_lowercase()) ;
	
	  

}

```


-------
# Result
#rust/result

>[!info] Result
> a data type that contains one of two types of data:
> 	- "successful" data
> 	- "error" data
> - used in scenarios where an action needs to be taken, but has the possibility of failure
> 	- copying a file
> 	- connecting to a website


definition
```rust
enum Result<T, E> {
	Ok(T),
	Err(E)
}
```

example
```rust
fn get_sound(name: &str) -> Result<SoundData, String> {
	if name == "alert" {
		Ok(SOundData::new("alert")),
		
	} else {
		Err("unable to find sound data".to_owned())
	}
}

let sound = get_sound("alert") ;
match sound {
	Ok(_) => println("sound data located") ,
	Err(e) => println!("error: {:?}", e) ,
}
```

>[!info] Recap
>- *Result* represents either success or failure
>		- *Ok(variable_name)* the operation was completed
>		- *Err(variable_name)* the operation failed
>- Useful when working with functionality that can porentially fail
>- Use `Result<T,E>` when working with results




Example
```rust
#[derive(Debug)]
enum MenuChoise {
	MainMenu,
	Start,
	Quit
}

  

fn get_choice(input: &str) -> Result<MenuChoise, String>{
	match input {
		"mainmenu" => Ok(MenuChoise::MainMenu),
		"start" => Ok(MenuChoise::Start),
		"quit" => Ok(MenuChoise::Quit),
		_ => Err("Menu choice not found".to_owned()),
	}
}


fn print_choice(choice: &MenuChoise) {
	println!("choice 3 (from fn): {:?}", choice) ;
}

fn main() {
	let choice_1= get_choice("mainmenu") ;
	println!("choice 1 = {:?}", choice_1) ;
	let choice_2 = get_choice("XXX") ;
	println!("choice 2 = {:?}", choice_2) ;
	let choice_3: Result<MenuChoise, _> = get_choice("start");
// print_choice(&choice3); --> it generates an error, because `get_choice()` returns Result not MenuChoice
// to handle that problem use `match`
	match choice_3 {
		Ok(inner_choice) => print_choice(&inner_choice),
		Err(e) => println!("error = {:?}", e) ,
	}
}
```

faster way to extract data wrapped into `Result` -> use   ==a question mark operator==

```rust
#[derive(Debug)]
enum MenuChoice {
	MainMenu,
	Start,
	Quit
}

fn get_choice(input: &str) -> Result<MenuChoice, String>{
	match input {
	"mainmenu" => Ok(MenuChoice::MainMenu),
	"start" => Ok(MenuChoice::Start),
	"quit" => Ok(MenuChoice::Quit),
	_ => Err("Menu choice not found".to_owned()),
	}
}

fn print_choice(choice: &MenuChoice) {
	println!("choice other (from fn): {:?}", choice) ;
}

// Result<(), String> `()` it is called unit type that just represent nothing
fn pick_choice(input: &str) -> Result<(), String> {
//`?` automatically perform a match operation
	let choice: MenuChoice = get_choice(input)?;
	// if Ok, inner data will get placed into `choice`
	//if Err, the error is going to get automatically returned
	// as the error from the function
	print_choice(&choice) ;
	//and return OK
	Ok(())
}


fn main() {
	let choice_1= get_choice("mainmenu") ;
	println!("choice 1 = {:?}", choice_1) ;

	let choice_2 = get_choice("XXX") ;
	println!("choice 2 = {:?}", choice_2) ;

	let choice_3: Result<MenuChoice, _> = get_choice("start");
	// print_choice(&choice3); --> it generates an error, because `get_choice()` returns Result not MenuChoice
	// to handle that problem use `match`
	match choice_3 {
		Ok(inner_choice) => print_choice(&inner_choice),
		Err(e) => println!("error = {:?}", e) ,
}


pick_choice("quit") ;

let e = pick_choice("end") ;
println!("error {:?}", e) ;
}


////// output
choice 1 = Ok(MainMenu)
choice 2 = Err("Menu choice not found")
choice other (from fn): Start
choice other (from fn): Quit
error Err("Menu choice not found")

```

---
```rust
struct Customer {
	age: i32,
}


fn canBuy(customer: &Customer) ->Result<(), String> {
	if customer.age < 21 {
		Err("You doesn't hhave at least 21!!".to_owned())
	} else {
		Ok(())
	}
}

fn main() {
	let ashley = Customer {age: 21} ;
	let purchased = canBuy(&ashley) ;
	println!("{:?}", purchased) ;
}
```

----
## Result and Question Mark
```rust
enum Position {
 Maintenance,
 Manager,
 AssemblyTech,
 Marketing
}

enum Status {
 Active,
 Terminated,
 }

struct Employee{
 position: Position,
 status: Status,
 }

  

fn may_enter_building(emp: &Employee) -> Result<(), String> {
 match emp.status {
 Status::Terminated => return Err("terminated".to_owned()),
 _ => (),
 };

 match emp.position {
  Position::Manager => Ok(()),
  Position::Marketing => Ok(()),
  _  => Err("No access".to_owned()),
 }
}

fn print_access(emp: &Employee) -> Result<(), String> {
	let attemp_access = may_enter_building(emp)? ;
	println!("access ok") ;
	Ok(())
}

fn main(){
	let manager = Employee {
		position: Position::AssemblyTech,
		status: Status::Active,
	} ;

	match print_access(&manager) {
		Err(e) => println!("access denied: {:?}", e),
		_ => (),
	}
}
```

----------
# Hashmap
#rust/hashmap 

>[!info] hashmap
>- collection that stores data as key-value pairs
>	- data is located using the "key"
>	- the data is the "value"
>- similar to definitions in a dictionary
>- very fast to retrieve data using the key
>- data are stored in random 


EXAMPLE
```rust
let mut people = HashMap::new();
people.insert("Susan", 21);
people.insert("Ed", 34);
people.insert("Will", 13);
people.remove("Susan") ;

match people.get("Ed") {
	Some(age) => println!("age = {:?}", age),
	None => println("not found"),
}

for(person, age) in people.iter() {
	println!("person = {:?}, age={:?}", person, age) ;
}

for person in people.key() {
	println!("person = {:?}", person) ;
}

for age in people.values() {
	println!("age={:?}", age) ;
}
```






























