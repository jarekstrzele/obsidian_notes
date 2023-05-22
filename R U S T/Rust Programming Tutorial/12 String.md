#rust/string 
https://www.youtube.com/watch?v=ABYdoxzNJJ8
[[_ Rust Programming Tutorial]]


--------------
# String

```rust
fn main(){
 let mut my_string = String::from("My first string in Rust") ;

  println!("Length {}", my_string.len()) ;
  println!("isEmpty? {}", my_string.is_empty()) ;
   
  for token in my_string.split_whitespace(){
    println!("{}", token) ;
  }

  println!("Does the string contain 'in'? {}", my_string.contains("in"));

  my_string.push_str(". This is a new text in the old string.") ;
  println!("After .push:\n {} ", my_string) ;
}

output
 cargo run
    Blocking waiting for file lock on build directory
   Compiling my-project v0.1.0 (/home/runner/rustfirst)
    Finished dev [unoptimized + debuginfo] target(s) in 2.32s
     Running `target/debug/my-project`
Length 23
isEmpty? false
My
first
string
in
Rust
Does the string contain 'in'? true
After .push:
 My first string in Rust. This is a new text in the old string. 
 

```


--------
# String Methods
```rust
  
  

fn main() {
	/* replace */
	{
	let my_string = String::from("Rust is fantastic!") ;
	println!("After replace: {}", my_string.replace("fantastic", "great")) ;
	}
/* output 
After replace: Rust is great!
*/
  
	{
	/* lines */
	let my_string = String::from("The weather is\nnice\noutside mate") ;
	for line in my_string.lines() {
		println!("[ {} ]", line) ;
	}
/*output 
[ The weather is ]
[ nice ]
[ outside mate ]
*/
}

  

/* split */
	{
	let my_string = String::from("leave+a+like+if+you+enjoyed!") ;
	let tokens: Vec<&str> = my_string.split("+").collect() ;
	println!("At index 3: {}", tokens[2]) ;
/*output 
At index 3: like
*/
	
	}

  

	/*trim */
	{
	let my_string = String::from(" My name is Domeniv \n\r") ;
	println!("Before trim: {}", my_string);
	println!("After trim: {}", my_string.trim()) ; // doesn't change the my_string
	println!("Before after trim(): {}", my_string);
/* output 
Before trim:      My name is Domeniv    

After trim: My name is Domeniv
Before after trim():      My name is Domeniv    

	*/
	}

  

	/* chars */
	{
	let my_string = String::from("decode on youtube") ;
	println!("{}", my_string) ;
	/* get character at index */
	match my_string.chars().nth(4) {
		Some(c) => println!("Char at index 4: {}", c ),
		None => println!("No character at index 4.")
	}
/* 
output

decode on youtube
Char at index 4: d
*/
}

}
```



