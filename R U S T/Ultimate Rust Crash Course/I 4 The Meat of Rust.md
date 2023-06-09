
[[_ Ultimate Rust Crash Course]]

# Structs
#rust/struct 
In other languages  you have classes, in Rust you have `struct`
```rust
struct RedFox{
	enemy: bool,
	life: u8,
}
```
- structs can have data fields, methods, and associated functions
- structs are named *CamelCase*
- instantiating a struct yu need to specify a value for every single field
```rust
let fox = RedFox {
	enemy: true,
	life: 70,
}
```
you would implement an associated function to use as a CONSTRUCTOR to create a struct with default values
```rust
impl RedFox {
	fn new() -> Self{
		Self {
			enemy: true,
			life: 70,
		}
	}
}
```
`new()` is **an associated  function** (like *class method* in other languages )
`Self` can be used in place of the struct name

to CREATE an instance of that struct:
```rust
let fox = RedFox::new();
let life_left = fox.life;
fox.enemy = false;
fox.some_method()
```
the scope operator in Rust is double colons `::`, and we use it to access parts of namespace-like things

METHODS are also DEFINED in the IMPLEMENTATION BLOCK:
```rust
impl RedFox{
	//associated function
	fn function() ...

	//method
	fn move(self) ..
	fn borrow(&self) ...
	fn mut_borrow(&mut self)
}
```

==NO STRUCT  INHERITANCE in Rust!!!!!==, because this gives us a better way to solve the problem we wish inheritance solved: TRAITS
#rust/traits 
==Rust takes the COMPOSITION over INHERITANCE APPROACH==


# Traits
>[!info] Trait
>- It is similar to in *interfaces* in other languages 
>-  it defines required behavior:
>		- **functions** that struct must implement
>		- **method** that struct must implement

```rust
struct RedFox{
	enemy: bool,
	life: u8,
}

trait Noisy {
	fn get_noise(&self) -> &str;
}

impl Noisy for RedFox {
	fn get_noise(&self) -> &str {
		"Meow?"
	}
}
```
we have traits, so ==we can start  writing GENERIC FUNCTIONS== that accept any value that implements the trait
```rust
//GENERIC FUNCTION
fn print_noise<T: Noisy>(item: T){
	println!("{}", item.get_noise()) ;
}
```
- the function takes a GENERIC  item of type `T` which is defined to be **anything that implements the Noisy trait**
- you can implement any `trait` for any `struct`

to implement the Noisy trait for the built-in type `u8`
```rust
impl Noisy for u8{
	fn get_noise(&self) -> &str("BYTE!")
}
```


```rust
fn main(){
	print_noise(5_u8) ; // prints "BYTE!"
}
```

#### `copy`
- a special trait
- types from the stack implement `copy` (integer, float, bool)
- types from the heap do not implement `copy`

==TRAITS implement INHERITANCE==, so  a trait can inherit from another trait
TRAITS can have default behaviors

![[traits_inheritance.excalidraw | 300]]

### **the default implementation**:
```rust
trait Run {
	fn run(&self) {
		println!("I'm running") ;
	}
}

struct Robot {}
impl Run for Robot {}

fn main(){
	let robot = RObot {} ;
	robot.run();
}
```

==No fields in Traits== 


```rust
// 1. Define a trait named `Bite`
// Define a single required method, `fn bite(self: &mut Self)`. We will call this method when we
// want to bite something. Once this trait is defined, you should be able to run the program with
// `cargo run` without any errors.
//

trait Bite {
	fn bite(self: &mut Self) ;
}
  

// 2. Now create a struct named Grapes with a field that tracks how many grapes are left. If you
// need a hint, look at how it was done for Carrot at the bottom of this file (you should probably
// use a different field, though).
//

#[derive(Debug)] // include this line right before your struct definition
struct Grapes {
	amount_left: f32,
}

// 3. Implement Bite for Grapes. When you bite a Grapes, subtract 1 from how many grapes are left.
// If you need a hint, look at how it was done for Carrot at the bottom of this file.

impl Bite for Grapes {
	fn bite(&mut self){
	self.amount_left *= 0.8 ; //self.percent_left - 1.0 ;
	}
}

fn main() {

	let mut carrot = Carrot { percent_left: 100.0 };
	carrot.bite();
	println!("I take a bite: {:?}", carrot);

	let mut grapes = Grapes { amount_left: 100.0 };
	grapes.bite();
	println!("Eat a grape: {:?}", grapes);

	fn bunny_nibbles<T: Bite>(item: &mut T) {
		item.bite();
		item.bite();
		item.bite();
	}

	bunny_nibbles(&mut carrot);
	println!("Bunny nibbles for awhile: {:?}", carrot);
}

#[derive(Debug)] // This enables using the debugging format string "{:?}"
struct Carrot {
	percent_left: f32,
}

impl Bite for Carrot {
	fn bite(self: &mut Self) {
	// Eat 20% of the remaining carrot. It may take awhile to eat it all...
	self.percent_left *= 0.8;
	}
}
```

-------
# Collections
## vector `Vec<T>`
It is a generic collection that holds a bunch of one type
```rust
let mut v: Vec<i32> = Vec::new();
//vector is like a stack
// add item
v.push(2);
v.push(4);
v.push(6);

//remove the item at the end of the vectora and returns it
let x = v.pop(); // x is 6

println!("{}", v[1]) ; // prints "4"

// MACRO to create a vector
let mut v = vec![2,4,6] ;

```

## HashMap `HashMap<K,V>`
It is a generic collection where you specify a type for the key and a type for the value.
You access the values by key (like DICTIONARY)
```rust
let mut h: HashMap<u8, bool> = HashMap::new() ;

h.insert(5, true) ;
h.insert(6, false) ;

//remove returns an Enum called OPTION
let have_five = h.remove(&5).unwrap();

```
==Dlaczego `&5` a nie `5`?==
- Jeśli użyjemy tylko `5` jako argumentu, oznaczałoby to, że próbujemy usunąć klucz, który jest równy `5`, a nie klucz przechowujący wartość `5`.
- `remove()` oczekuje referencji do klucza


other
`VecDeque` It  uses a ring buffer to implement a double-ended queue
`LinkedList, HashSet, BTreeMap, LinkedList, BinaryHeap, BTreeSet`

# Enum
Enums in Rust are more like algebraic data types in Haskell.

```rust
enum Color {
	Red,
	Green,
	Blue,
}

let color = Color::Red ;

enum DispenserItem {
	Empty,
	Ammo(u8),
	Thing(String, i32),
	Place {x: i32, y: i32},
}

use DispenserItem::* ;
let item = Empty ;
let item1 = Ammo(68) ;
let item2 = Things("hat".to_string(), 7) ;
let item3 = Place {x: 24, y: 48} ;



```

`Enum` can be any one of those,==BUT ONLY ONE AT A TIME.==

==you can implement functions and methods for an `enum`==
```rust
impl DispenserItem{
	fn display(&self){}
}
```


==You can also use `enum` with GENERICS==

### Option
e.g. `Option` is a generic `enum` in the standard library:
#rust/option 
```rust
enum Option<T> {
	Some(T),
	None,
}
```
`Option` represents when something is either absent or present

```rust
// if you manage with one value, you can use:
if let Some(x) = my_variable {
	println!("value is {}", x) ;
}

//MATCH EXPRESSION
match my_variable {
	Some(x) => {
	println!("value is {}", x)
	},
	None => { 
		println!("no value")
	},
}
```

OPTION
```rust
let mut x = None;
x = Some(5) ;
x.is_some(); //true
x.is_none(); //false
for i in x {println!("{}", i) ;} //print 5
```


### RESULT
#rust/result 
`Result` is used whenever something might have a useful result, or might have an error 
definition
```rust
#[must_use] //it makes a compiler warning to sulently drop a result
enum Result<T,E<{
	Ok(T),
	Err(E),
}
```

example
```rust
use std::fs::File;

fn main() {
	File::open("foo") ; //this returns Result because the file might not get opened successfully
}
```

```rust
use std::fs::File;

fn main() {
	let res = File::open("foo") ; //this returns Result because the file might not get opened successfully
	let f= res.unwrap() ; // if the Result is Ok(), it gives you the File struct that you wanted;; Err crashes the program
}
```
other option
```rust
use std::fs::File ;

fn main(){
	let res = File::open("foo") ;
	let 

}
```

