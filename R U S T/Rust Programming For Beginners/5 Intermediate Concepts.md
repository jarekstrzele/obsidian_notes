[[#Expressions]]
[[#Memory]]
[[#Ownership]]
[[#keyword `impl`]]


---
[[_ Rust Programming for Beginners]]

---
# Expressions
#rust/expression 
>- Rust is an expression-based language (most things are evaluated and return some value)
>- Expression values coalesce to a single point (can be used for nesting logic)

expression examples:
`if, match, >, ...`
```rust
let my_num = 3; 
let msg = match my_num{
   1 => "hello",
   _ => "goodbye"
}
```

```rust
enum Access {
  Admin,
  Manager,
  User,
  Guest
}
fn main(){

  //secret file: admins only
  let access_level = Access::User ;
  let can_access_file = match access_level{
    Access::Admin => true,
    _ => false
  } ;

println!("Can read a secret file? {:?}", can_access_file) ;
}
```


```rust
fn print_msg(gt_100: bool){
  match gt_100 {
    true => println!("It's big"),
    false => println!("It's small"),
  }
}

fn main(){
  let value = 100;
  let is_gt_100 = value > 100;
  print_msg(is_gt_100) ;
  
}

```


---
# Memory
#rust/memory 
*Memory uses addresses  & offsets.
Addresses are permanent, data differs
Offsets can be ised to "index" into some data*

>[!info] Memory
> - memory is stored using binary (bits: 0 or 1)
> - computer optimized for bytes (1 byte == 8 contiguous bits)
> -  all data in memory has an "address" 
> 	- used to locate data
> 	- always the same - only data changes
> - usually don't utilize address directly (variables handle most of the work)
>

>[!info] memory offsets (przesunięcia pamięci)
>	- item can be located at an address using an "offset"
>	- offsets begin at 0
>	- represent the number of bytes away from the original addres (normally deal with indexes instead)
>example:
>`Data[1]` 
>	-	address 4 (the variable name `data` automatically take care of the the address ),
>	- offset 1




-------------
# Ownership
#rust/ownership 

>[!important] Ownership
>- it is what allows us:
>	- to execute code in a performant manner
>	- help ensure that compile the code executes correctly inder various circumstances


>[!info] Managing memory
>	- program must track memory  ( if they fail to do so, a "leak" occurs) ([[memory_leak]])
>	- Rust utilizes what is called an ownership model to manage memory (prevent the memory leak ) (the "owner" of memory is responsible for cleaning up the memory)
>	- memory can either be =="moved"== or =="borrowed"==

EXAMPLE
there is a problem with this program, because we are calling display light twice
```rust
enum Light {
	Bright,
	Dull,
}

fn display_light(light: Light){
	match light {
		Light::Bright => println!("bright"),
		Light::Dull => println!("dull"),
	}
}

fn main(){
	let dull = Light::Dull ;
	display_light(dull) ;
	display_light(dull) ;
}
```
The error is due to the ownership model. 
When we create this new ligth and assign it to the doll variable, it is owned by the `main` function.
When we call `display_light(dull) ;` this dull light is being MOVED into a new function, so this `dull` light will be own by `display_light` function

==any function that owns data is required to delete the data once the function completes== so
the light will get deleted once the `display_light` finishes
Because the `dull` light is deleted, it's no longer available for use again in the `main` function

IF YOU WANT TO USE the `dull` light more the once use BORROW instead of MOVING
```rust
enum Light {
	Bright,
	Dull,
}

fn display_light(light: &Light){
	match light {
		Light::Bright => println!("bright"),
		Light::Dull => println!("dull"),
	}
}

fn main(){
	let dull = Light::Dull ;
	display_light(&dull) ;
	display_light(&dull) ;
}
```

### `&` the ampersand symbol in Rust indicates that we are borrowing data /referencing data
```rust
fn maim(){
let dull = Light::Dull;
}
```
We create a`dull` variable
and the `main` function will immediately BECOME THE OWNER

```rust
display_light(&dull) ;
```
- we borrow the `dull` light and send the reference to the function, but `main` function is still the owner
- after the `display_light` function the control go back to `main`
- 

> [!info] Recap
> - memory must be managed in some way to prevent leaks
> - Rust uses "ownership" to accomplish memory management
> 	- the "owner" of data must clean up the memory
> 	- this occurs automatically at the end of the scope
> - Default behavior is to "MOVE" memory to a new owner (use an **apersand** `&` to allow code to "BORROW" memory)

```rust

struct Book{
  pages: i32,
  rating: i32,
}

//fn display_page_count(book: Book){
fn display_page_count(book: &Book){
  println!("pages = {:?}", book.pages) ;
}

//fn display_rating(book: Book){
fn display_rating(book: &Book){
  println!("rating = {:?}", book.rating)
}

fn main(){
  let book = Book{
    pages: 5,
    rating: 9,
  };

// MOVING OWNERSHIP
	//display_page_count(book) ; //this function takes the ownership of `book`, and then when the function will finish its execution, `book` will be deleted so
  //display_rating(book) ; // this function calling generates an error, because book doesn't exist anymore

// BORROWING OWNERSHIP
  display_page_count(&book) ;
  display_rating(&book) ;
}
```



------
# keyword `impl`
#rust/impl

```rust
struct Temperature {
  degrees_f: f64,
}

impl Temperature{
  fn freezing() -> Self {
    Self {degrees_f: 32.0}
  }

  fn boiling() -> Self {
    Self {degrees_f: 222.0}
  }

  fn show_temp(&self){
    println!("{:?} degrees F", self.degrees_f) ;
  }
}
fn main(){

  let t = Temperature{degrees_f: 99.1} ;
  t.show_temp() ;

  let c = Temperature::freezing() ;
  c.show_temp() ;

  let h = Temperature::boiling() ;
  h.show_temp() ;
  
}

output
99.1 degrees F
32.0 degrees F
222.0 degrees F
```










