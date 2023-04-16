#rust #server 

# HTTP/1.1
- L7 Protocol
- sent over TCP (servers communicate by exchanging individual messages instead of streaming data)
- message based:
	- messages sent by the client (browser) are called **requests**
		- starts with: method (e.g. `GET`)
		- next path
		- next protocol (e.g. `HTTP`)
		- next a new line
		- and headers (`key:value` format)
		- next two new lines
	- messages sent by the server as an answer are called **responses**
		- starts with the protocol  and status code and reason fraus (`HTTP/1.1 200  OK`)
		- next line: list of headers 
		- next two new lines
		- and body (any format: html, json, js, ...)

REQUEST:
```
GET /search?name=abc HTTP/1.1 
Accept: text/html
```
RESPONSE:
```
HTTP/1.1 200 OK
Content-Type: text/html

<!DOCTYPE html>
<html land="en">
....
</html>
```

![[rust-server.excalidraw | 660]]


-------------
# STRUCTS
### `cargo new server`

main.hs (our interfejs project)
```rust
fn main() {

	let server = Server::new("127.0.0.1:8080") ;
	server.run() ;
}
```

`Server`  will be a struct.

>[!info] `STRUCT`
>it is a custom data type that lets you group tohether related data.
>(kind of a class in object oriented languages)
>```rust
>struct MyStruct{ 
>	attr: Type,
>}
>
>impl MyStruct{
>	methods
>}
>```

### methods and associated functions
> **methods** are function defined inside the `struct`
> **methods** in the Rust take a special first parameter called `self`
> `self` represents the instance of the struct the method is being called on

>**associated functions** like a static functions in OOP - they are associated with the struct type, but they don't need an instance (e.g. `new`)
>use `::` sythax to access associated functions


main.rs
```rust
fn main() {

	let server = Server::new("127.0.0.1:8080") ;
	server.run() ;
}

struct Server{
	addr: String,
}


impl Server{
	//associated function
	// fn new (addr: String) -> Server
	// Self - it is an alias to the struct type
	fn new(addr: String) -> Self{
	// Self == Server
	// Server { addr }
		Self {
		//addr: addr // are the same so you can omitt
			addr
		}
	}
	
	fn run(self){
	//this function takes ownership of the entire struct
	// because ot tales ownership pf the sef variable
	// run(&self) - in this case self does not take a ownership
	// of the struct
	}
	 
	
	}
```


this code generates an error:
```rust
let server = Server::new("127.0.0.1:8080") ;
   |                  ----------- ^^^^^^^^^^^^^^^^- help: try using a conversion method: `.to_string()`
   |                  |           |
   |                  |           expected struct `String`, found `&str`
   |                  arguments to this function are incorrect
```
expecting `String` but found `&str`
so `"127.0.0.1:8080"` is not a string

## Strings
#rust/string
`&str` it is called ==a string slice==
	**string slice** is an immutable reference to a part of a string (like `string view` in C++)

```rust
fn main() {
// let server = Server::new("127.0.0.1:8080") ;
// server.run() ;
let string = String::from("127.0.0.1:8080") ;
let string_slice = &string[10..14] ; //8080; you borrow an existing string
// [10..14] == [10..]
// [0..3] == [..3]

//dbg!(string) ; // this is incorrect because you borrowed the string
dbg!(&string) ;
dbg!(string_slice) ;
}

output:
[src/main.rs:9] &string = "127.0.0.1:8080"
[src/main.rs:10] string_slice = "8080"
```

#### example:
- you have allocated some strings on the heap
- the strings are from 0 bytw to 11 byte 
	- `0 - A`
	- `1 - B`
	- `2 -C`
	- ..
	- `6 - space`
	- `7 - G`
	- ...
	- `9 - I`
	- `10 -`
	- `11 -`
- represent this on the stack:
	- length: 10
	- capacity: 12 (all the bytes that you allocated for the string):
		- if you push too many characters and they cannot fit the free capacity,
			- a new buffer that is bigger will be allocated somewhere else on the heap and
			- the entire string will be moved there, 		-  
	- ptr (pointer) indicates/points `0-A` the beginning of the string
- you want to read last three characters of the string `G(7), H(8), I(9)`:
	- you can copy last chacaracters but you also can use `&str`
	- `&str` on the stack (VERY EFFICIENT WAY):
		- length: 3
		- ptr: `G(7)`

### convert a string into a string slice
- The compiler can transparently convert a string into a string slice for us
- if we want to pass a string to a function that actually accepts the strings slice, the compiler will convert the string into a string slice and pass that to the function
```rust
let string = String::from("127.0.0.1:8080") ;

let string_slice = &string[10..14] ; //8080
let string_borrow: &str = &string ; // the compilet will just convert `&string` into s string slice that points to the entire string

```


### string literals
`let string_literal = "1234" ;` this literal string is known at compile time , it will bake it into the binary itself; there will be some region in memory where the string actually leaves

**normal strings** can be expended or they can shrink dynamically at runtime
**string slices** are IMMUTABLE;  `let string_literal="1234"` is immutable because we specified in its entirety at compule time,
so a string slice would be an immutable view of this entire string













