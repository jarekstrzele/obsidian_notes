[[_ LetsGetRusty Ultimate Rust Lang Tutorial]]


### `cargo new guessing_game`

- variable are immutable by default
add to `Cargo.toml` some dependencies:
```toml
[dependencies]
rand = "0.8.5"
colored = "2.0.0"
```
and now 
##### `cargo build`


```rust
use std::io ;
use std::cmp::Ordering ; // It is a Enum: Less, Equal, Greater
use rand::Rng;
use colored::*;

fn main() {
	println!("Guessing the number!");
//thread_rng() - gives a random number generator
// gen_range() - method that will produce random number

//let secret_number = rand::thread_rng().gen_range(1);

let secret_number = rand::thread_rng().gen_range(1..=100); // Generate a random number between 1 and 100

println!("Secret number is {}", secret_number) ;

loop {

println!("Please input your guess.");

  
  

let mut guess: String = String::new() ; // new() is a static method

  

io::stdin()

.read_line(&mut guess)

.expect("Failed to read line") ; //read_line returns Result type

// let guess: u32 = guess

// .trim()

// .parse()

// .expect("Please type a number!") ; // parse return Result type

let guess: u32 = match guess.trim().parse(){

Ok(num) => num,

Err(_) => {

println!("Type a number!") ;

continue;

}

} ;

  

println!("You guessed: {}", guess) ;

  

match guess.cmp(&secret_number) {

Ordering::Less => println!("{}", "Too small".red()),

Ordering::Greater => println!("{}", "Too big".red()),

Ordering::Equal => {

println!("{}", "You win".green());

break ;

}

}

  

}

}
```



