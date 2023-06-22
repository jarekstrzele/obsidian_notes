#rust #youtube 
https://www.youtube.com/watch?v=ygL_xcavzQ4


[[#generate a project]]
[[#app 'what is your name']]
[[#Constant]]
[[#shadowing]]
[[#Types]]
[[#Random]]
[[#Vectors]]
[[#Function]]
[[#Generics]]
[[#Modules, crates]]
[[#Memory]]
[[#hashmap]]




--------
# generate a project

#### `cargo new rust_tutorial`

at the beginning of a file write
### `#![allow(unsused)]`

`use std::io ;` 
`use std::io::{Write, BufReader, BufRead, ErrorKind} ;`
`use std::fs::File ;`
`use std::cmp::Ordering ;`

`use rand::Rng ;` random numbers ==> this line of the code generates an error, so
go to `Cargo.toml` file and under `[dependecies]` put `rand = "0.8.5"`

vs code - `rust-analyzer`

https://crates.io/

----------
# app 'what is your name'

```rust
fn main() {
	println!("What is your name?") ;
	let mut name = String::new() ;
	io::stdin().read_line(&mut name).expect("Didn't Receive Input") ;
	println!("Hello, world!");
}
```

`&mut name` this is a reference to a variable
`read_line` returns `Result`
`Result` it is a `enum` and *enum* it is a type that has a fixed number of possible values
*Result* can return `Ok` or `Err`

```rust
fn main() {
	println!("What is your name?") ;
	let mut name = String::new() ;
	let greeting = "Nice to meet you" ;
	io::stdin().read_line(&mut name).expect("Didn't Receive Input") ;
	println!("Hello, {}! {}", name.trim_end(), greeting);
}
```

--------
# Constant
`const ONE_MIL: u32 = 1_000_000 ;`
`const PI: f32 = 3141592 ;`

---
# shadowing
define variables with the same name but different data types
```rust
let age: &str = "47" ;
let mut age: u32 = age.trim().parse().expect("Age was't assigne a number") ;
age = age + 1;
println!("I'm {} and I want ${}", age, ONE_MIL)

```

----
# Types
Rust is **statically typed** which means all the types must be defined (compiler will defined them or you define them)


```rust
fn main() {
	println!("Max u32: {}", u32::MAX) ;
	println!("Max u64: {}", u64::MAX) ;
	println!("Max u128: {}", u128::MAX) ;
	println!("Max f32: {}", f32::MAX) ;
	println!("Max f128: {}", f64::MAX) ;
}

output
Max u32: 4294967295
Max u64: 18446744073709551615
Max u128: 340282366920938463463374607431768211455
Max f32: 340282350000000000000000000000000000000
Max f128: 179769313486231570000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
 *  Terminal will be reused by tasks, press any key to close it. 
```


`f32`
`f64`
`u32`
`u64`

---

# Random
#rust/random

```rust
use rand::Rng ;


fn main() {
	let random_num: i32 = rand::thread_rng().gen_range(1..6+1) ;
	println!("random number {:?}", random_num) ;

}
```

1. `rand::thread_rng()` - Tworzy generator liczb losowych, który jest lokalny dla bieżącego wątku. Jest to inicjalizacja generatora losowego.
    
2. `.gen_range(1..6+1)` - Wywołuje metodę `gen_range` na obiekcie generatora losowego. Metoda ta generuje losową liczbę z podanego zakresu (włącznie z dolnym limitem, ale wyłączając górny limit).


```rust
#![allow(unused)]
use std::io ;
use rand::Rng ;
use std::io::{Write, BufReader, BufRead, ErrorKind} ;
use std::fs::File ;
use std::cmp::Ordering ;

fn main() {
	let random_num: i32 = rand::thread_rng().gen_range(1..6+1) ;
	println!("random number {:?}", random_num) ;
	let st3: String = String::from("x r t b h k k a m c") ;
	let mut v1: Vec<char> = st3.chars().collect() ;
	println!("{:?}", st3.chars()) ;
	v1.sort();
	v1.dedup(); // delete duplicate
	for char in v1 {
		print!("{char}") ;
	}
	let st4: &str = "Random string" ;
	let mut st5: String = st4.to_string();
	println!("{}", st5);
	let byte_arr1: &[u8] = st5.as_bytes() ;
	println!("byte arr {:?}", byte_arr1) ;
	let st6: &str = &st5[0..6] ;
	println!("st6 {:?}", st6) ;
	println!("string length : {}", st6.len()) ;
	st5.clear();

	let st6: String = String::from("Just some ") ;
	let st7: String = String::from(" words") ;
	let st8: String = st6 + &st7 ;
	for char in st8.bytes(){
		print!("{}", char) ;
	}
	println!("\n{st8}") ;

// println!("\n{st6}") ; // generates some errors
}


-- output
$ cargo run
   Compiling rust_tutorial v0.1.0 (/home/jarek/Desktop/Prog/rust-simple/rust_tutorial)
    Finished dev [unoptimized + debuginfo] target(s) in 0.20s
     Running `target/debug/rust_tutorial`
random number 6
Chars(['x', ' ', 'r', ' ', 't', ' ', 'b', ' ', 'h', ' ', 'k', ' ', 'k', ' ', 'a', ' ', 'm', ' ', 'c'])
 abchkmrtxRandom string
byte arr [82, 97, 110, 100, 111, 109, 32, 115, 116, 114, 105, 110, 103]
st6 "Random"
string length : 6
74117115116321151111091013232119111114100115
Just some  words
```


----
# Vectors 
```rust
pub fn vec_example() {
	let vec: Vec<i32> = Vec::new() ;
	let mut vec2: Vec<i32> = vec![10,20,30,40] ;
	vec2.push(5) ;
	let first = vec2[0] ;
	println!("1st: {}", first) ;
	let second: &i32 = &vec2[1] ; // it reads a value
	println!("second: {}", second);
	let sec2:i32 = vec2[1] ; // it copies a value
	println!("second: {}", sec2);

	match vec2.get(1){ //get() returns Option type
		Some(second) => println!("2nd : {}", second),
		None => println!("No 2nd value"),
}

for i in &mut vec2 {
	*i *= 2 ;
}

println!("------------") ;
for i in &vec2{
	println!("{}", i) ;
}
println!("Vec length {}", vec2.len()) ;
println!("Pop: {:?} ", vec2.pop()) ;
}

--- output

```


-----
# Function
#rust/function 

```rust
pub fn function_examples(){

let num_list = vec![1,2,3,4,5] ;
println!("Sum of list = {}", sum_list(&num_list)) ;
}

fn sum_list(list: &[i32]) -> i32 {
	let mut sum = 0 ;
	for &val in list.iter(){
		sum += &val ;
	}
sum
}
```


---------
# Generics
**generic types** we can specify the data type to be used at a later time 

YOU CAN'T write that way:
```rust
fn get_sum_gen(a: T, y: T) -> T {
	x + y
}
```

but this code is correct:
```rust
pub fn generics_examples(){
	println!("2 + 4 = {}",get_sum_gen(2, 4)) ;
	println!("2.0 + 4.0 = {}",get_sum_gen(2, 4)) ;
}

use std::ops::Add;

fn get_sum_gen<T: Add<Output = T>>(x: T, y: T) -> T{
	x + y
}
```

## generic struct
```rust
pub fn generics_examples(){

	let rec: Rectangle1<i32, f64> = Rectangle1{length: 4, height: 10.5};
	println!("{:?}", rec) ;
}

#[derive(Debug)]
struct Rectangle1<T, U>{
	length: T,
	height: U,
}
```

```rust
pub fn generics_examples(){
	let rec1: Rectangle1<i32, f64> = Rectangle1{length: 4, height: 10.5};
	println!("{:?}", rec1) ;
	let rec: Rectangle = Shape::new(10.50, 10.0) ;
	println!("area {}", rec.area()) ;
}

#[derive(Debug)]
struct Rectangle1<T, U>{
	length: T,
	height: U,
}

// --------------------

// ------------------

struct Rectangle{

	length: f32,
	width: f32,
}

impl Shape for Rectangle {
	fn new(length: f32, width: f32) -> Rectangle {
		Rectangle {length, width}
	}

	fn area(&self)-> f32{
		self.length * self.width
	}
}

trait Shape {
	fn new(length: f32, width: f32) -> Self ;
	fn area(&self) -> f32 ;
}

use std::ops::Add;
fn get_sum_gen<T: Add<Output = T>>(x: T, y: T) -> T{
	x + y
}
```

------
# Modules, crates
#rust/module 
#rust/crate 

>[!info] crates
>modules that produce a library or executable

>[!info] modules
>organize and handle privacy

>[!info] package
> build, test and share crates

>[!info] paths
>a way of naming  an item such as a struct , function ...

in `main.rs`
```rust
mod restaurant;
use crate::restaurant::order_food;

fn main() {
	order_food() ;
}
```


in `src` > a new folder `restaurant` > a new file `mod.rs`
```rust
mod pizza_order {
    pub struct Pizza{
        pub dough: String,
        pub cheese: String,
        pub topping: String,
    }

    impl Pizza {
        pub fn lunch(topping: &str) -> Pizza{
            Pizza {
               dough: String::from("regular dough"),
               cheese: String::from("mozzarella"),
               topping: String::from(topping),
            }
        }
    }

	pub mod help_customer{
        fn seat_at_table(){
            println!("Customer seated at table") ;
        }

        pub fn take_order(){
            seat_at_table();
            let cust_pizza: super::Pizza = 
                super::Pizza::lunch("veggies") ;
            serve_customer(cust_pizza) ;
        }

        fn serve_customer(cust_pizza: super::Pizza){
            println!("the customer is erved a regular pizza with {}", cust_pizza.topping) ;
        }
    }

}

pub fn order_food(){
    crate::restaurant::pizza_order::help_customer::take_order();
}



```




---
# Memory
#rust/ownership 
>[!info] managing memory - ownership
>- memory is managed by the system of ownership with rules that are checked at compile time
>- **rules**:
>	- each value has its owner
>	- one owner at any one time 
>	- whenever the owner goes out of scope, the value is going to disapear

>[!info] stack
>
> - store values in last in first out format LIFO
> - stack data must have a defined size

>[!info] heap
>- when you are putting data on the heap you request a certain amount of space and 
>- the operating system is going to find space that is available and then it's going to return an address for that space and that reference to the space in memory is going to be called a **pointer**
>- a pointer is like an address now

example of moving ownership
```rust
fn main(){
	let str1 = String::from("world") ;
	// let str2 = str1 ;
	// println!("Hello {}", str1) ; 
	// it generates error
	//   ---- move occurs because `str1` has type `String`, which does not implement the `Copy` trait

	let str2 : str1.clone() ;
	println!("Hello {}", str1) ; 
	
	
}
```

------
# hashmap

```rust
use std::collections::HashMap ;

pub fn hashmap_example(){
	let mut heroes = HashMap::new() ;
	heroes.insert("Superman", "Clark Kent") ;
	heroes.insert("Batman", "Bruce Wayne") ;
	heroes.insert("The Flash", "Barry Allen") ;

	for (key, value) in heroes.iter(){
		println!("{} = {}", key, value) ;
	}
	println!("length {}", heroes.len()) ;

	if heroes.contains_key(&"Batman"){
		let the_batman = heroes.get(&"Batman");
		println!("the batman {:?}", the_batman) ;

	match the_batman {
		Some(x) => println!("Batmanis a hero!!"),
		None => println!("Batman is not a hero"),
	}
	}
}
```


--------
# Errors

```rust
fn main(){
	panic!("terrible error") ;
}
--output
thread 'main' panicked at 'Terrible error', src/errors_my.rs:4:5
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
```

```rust
use std::fs::File ;
use std::io::{BufReader, Write, BufRead} ;

pub fn errors_example(){
	let path = "lines.txt" ;
	let output = File::create(path) ;
	let mut output = match output { 
		Ok(file) => file,
		Err(error) => { panic!("Problem creating file: {:?}", error); } 
};

	write!(output, "Just some\nRandom words").expect("Fail to write to file") ;
	let input = File::open(path).unwrap(); 
	let buffered = BufReader::new(input);


```
- makro `write!` pochodzi z modułu `std::io::Write`
- `.expect()` - jeśli  operacja zapisu zakończy się  niepowodzeniem, metoda ta spowoduje przerwanie programu i wyświetli się komunikat "Fail to write to file"

`unwrap()` 
#rust/unwrap 
- metoda dostępna dla typu `Result<T, E>` , 
- metoda ta "rozpakowuje" wartość z  z `Result`, zwraca wartość sukcesu, jeśli wynik jest `Ok` lub `panic!`, jeśli wynik jest `Err`

`BufReader`
#rust/bufreader 
- struktura z modułu `std:io`
- zapewnia buforowanie odczytu danych z danego źródła (np. z pliku)
- optymalizuje  odczyt danych redukując ilość bezpośrednich operacji odczytu 
	- `BufReader` przechowuje pewien bufor w pamięci, a następnie dokonuje operacji odczytu z tego bufora
	- `let buffered = BufReader::new(input)` 
		- tworzymy nową instancję BufReader
		- instancja będzie buforować odczyt z pliku reprezentowanego przez `input`

```rust
let buffered = BufReader::new(input);

for line in buffered.lines(){
	println!("{}", line.unwrap()) ;
}
```

`lines()` -  zwraca `Result` type  (iterator)

--------
# iterators
#rust/iterator 
>[!info] iterator
>it can help us cycle through values in:
>	- arrays
>	- vectors
>	- map
>	- ...

iterate through values by borrowing them
```rust
pub fn iter_example(){
	let mut arr_it = [1,2,3] ;
	for val in arr_it.iter() {
		println!("{}", val) ;
	}

	// `for val in arr_it {}` 
	//  this code automatically generate an iterator  
	
	// create your own iterator
	let mut iter1 = arr_it.iter() ;
	println!("1st: {:?} ", iter1.next()) ;
	println!("2nd: {:?} ", iter1.next()) ;
	println!("3rd: {:?} ", iter1.next()) ;
	println!("4th: {:?} ", iter1.next()) ;
}

/// output
1
2
3
1st: Some(1) 
2nd: Some(2) 
3rd: Some(3) 
4th: None 
```

-----------
# Closure
#rust/closure 

>[!info] closure
>It is a function without a name 
>`let var_name = |params| -> return_type {BODY}`

## basic example - closure
```rust
let can_vote =|age: i32| {
	age >= 18
} ;

println!("Can vote: {}", can_vote(8)) ;

- output -
Can vote: false
```

## more advance example - closure

```rust
pub fn closure_example(){
	let mut samp1 = 5;
	let print_var = || println!(
		"samp1 = {}", samp1) ;
		print_var();
	  
	samp1 = 10 ;
	let mut change_var = || samp1 += 1;
	change_var() ;
	println!("Sampl1 = {}", samp1) ;
	samp1 = 10;
	println!("samp1 = {}", samp1)
}

--- ouput

samp1 = 5
Sampl1 = 11
samp1 = 10
```

## function as argument - closure

```rust
pub fn closure_example(){
	fn use_func<T>(a: i32, b: i32, func: T) -> i32
		where T: Fn(i32, i32) -> i32 {
			func(a, b)
}

	let sum = |a, b| a + b ;
	let prod = |a, b| a * b ;
	println!("5+4={}", use_func(5, 4, sum)) ;
	println!("5*4={}", use_func(5, 4, prod)) ;
}
```


----------
# Pointer `&`
#rust/pointer

>[!info] pointer
> it is an address to a location in memory

- string
- vectors
- &
## smart pointer:
W języku Rust istnieją tzw. "smart pointery" (inteligentne wskaźniki), które są strukturami danych zapewniającymi pewne dodatkowe funkcjonalności w zakresie zarządzania pamięcią. Dwa najważniejsze smart pointery w Rust to `Box<T>` i `Rc<T>`.

1. `Box<T>` to smart pointer reprezentujący własność (ownership) na alokowanym na stercie (heap) obiekcie typu `T`. `Box<T>` zapewnia statyczne rozmiary i jest używany, gdy chcemy przechowywać dane na stercie, a nie na stosie. `Box<T>` gwarantuje, że obiekt zostanie zwolniony z pamięci po opuszczeniu zakresu.
    
2. `Rc<T>` (Reference Counted) to smart pointer reprezentujący współdzieloną (shared) własność na obiekcie typu `T`. `Rc<T>` umożliwia wielokrotne posiadanie niezmiennej referencji do tego samego obiektu. Zlicza ilość referencji do obiektu i automatycznie zwalnia pamięć, gdy ostatnia referencja jest usuwana.
    

Oba smart pointery są często używane w Rust do zarządzania pamięcią w sposób bezpieczny i bez konieczności ręcznego zwalniania zasobów. Wybór między nimi zależy od potrzeb i wymagań konkretnego przypadku.

Warto zaznaczyć, że Rust również zapewnia wskaźniki surowe (raw pointers) `*const T` i `*mut T`, ale ich użycie jest bardziej ryzykowne i wymaga ostrożności związanej z bezpieczeństwem. Wskaźniki surowe są rzadziej stosowane i zazwyczaj używane są do interakcji z kodem niskiego poziomu lub do tworzenia bezpiecznych abstrakcji wewnątrz zaawansowanych bibliotek.


>[!info] smart pointer
>- own data and have some  function for manipulating that data

### Box
binary tree structure utilizing box
[[Box]]

>[!info] box
>- store data on ==the heap== instead of the stack

**stack** 
- stores values in LIFO
- data on the stack must have a defined fixed size
```rust
pub fn box_example(){
	let b_int1 = Box::new(10) ;
	println!("b_int1 = {} ", b_int1) ;
}
```


```rust
pub fn box_example(){

	struct TreeNode<T>{
	// pub left: TreeNode<T>,
	// pub tight: TreeNode<T>,
		pub left: Option<Box<TreeNode<T>>>,
		pub right: Option<Box<TreeNode<T>>>,
		pub key: T,
	}

	impl<T> TreeNode<T>{
		pub fn new(key: T) -> Self{
		TreeNode { left: None, right: None, key,}
	}

	pub fn left(mut self, node: TreeNode<T>) -> Self {
	self.left = Some(Box::new(node)) ;
	self
	}
	

	pub fn right(mut self, node: TreeNode<T>) -> Self {
	self.right = Some(Box::new(node)) ;
	self
	}
	}

	let node1 = TreeNode::new(1)
		.left(TreeNode::new(2))
		.right(TreeNode::new(3)) ;
}
```


---------
# Concurrency
simulate a bank transactions

Common problems with parallel programming involve:
- threads are accessing data in the wrong order
- threads are blocked from executing because of confusion


1. `std::thread`: Ta biblioteka umożliwia tworzenie i zarządzanie wątkami w Rust. Daje programiście możliwość tworzenia nowych wątków, zarządzania ich cyklami życia, komunikacji między wątkami i synchronizacji dostępu do danych. Umożliwia tworzenie współbieżnych programów i wykonywanie równoległych operacji. Przykładowe funkcje z tej biblioteki to `spawn`, `join`, `sleep` itp.
    
2. `std::time::Duration`: Ta biblioteka umożliwia manipulację czasem w Rust. Zapewnia typ `Duration`, który reprezentuje okres czasu. Można go używać do wykonywania operacji na czasie, takich jak oczekiwanie przez określony czas, mierzenie czasu trwania operacji, tworzenie opóźnień itp. Udostępnia różne metody i operatory, takie jak `from_secs`, `as_secs`, `add`, `sub` itp., które umożliwiają wygodną manipulację czasem.


```rust
use std::thread;
use std::time::Duration;

pub fn tread_example(){

	// create a thread
	let thread_1 = thread::spawn( || {
		for i in 1..10 {
			println!("Spawned thread : {} ", i) ;
			thread::sleep(Duration::from_millis(1))
		};
	});

	for i in 1..8{
		println!("Main thread : {} ", i);
		thread::sleep(Duration::from_millis(1));
	} ;
	
	thread_1.join().unwrap() ; // two thread will end its works
}

-- out put
Main thread : 1 
Spawned thread : 1 
Main thread : 2 
Spawned thread : 2 
Main thread : 3 
Spawned thread : 3 
Main thread : 4 
Spawned thread : 4 
Main thread : 5 
Spawned thread : 5 
Main thread : 6 
Spawned thread : 6 
Main thread : 7 
Spawned thread : 7 
Spawned thread : 8 
Spawned thread : 9 
```


