[[_ LetsGetRusty Ultimate Rust Lang Tutorial]]

`use std::env` - a user will be able to pass in a string and a file name

`collect()` - initializes a vector, makes a vector from args passed at invocation
`env::args()` - returns an iterator that allows iterating over the command-line arguments
`env::args().collect()` - it collects the command-line args and put them into the vector

```rust
use std::env;

fn main() {
	let args: Vec<String> = env::args().collect() ;
	println!("{:?}", args) ;
}
```

`cargo run`  -> `["target/debug/minigrep"]` a path to our binary
```bash
$ cargo run first dua
    Finished dev [unoptimized + debuginfo] target(s) in 0.00s
     Running `target/debug/minigrep first dua`
["target/debug/minigrep", "first", "dua"]
```

---
create a file `poem.txt` with some text
`main.rs`
```rust
use std::env;
use std::fs;

fn main() {
	let args: Vec<String> = env::args().collect() ;
	let query = &args[1] ;
	let filename = &args[2] ;

	println!("Searching for {}", query) ;
	println!("in file {}", filename) ;

	let contents = fs::read_to_string(filename).expect("Something went wrong reading the file") ;
	println!("With text: \n{}", contents) ;
}
```


## refactoring

### too many responsibilities in the `main` file
first version
```rust
use std::env;
use std::fs;

fn main() {
	let args: Vec<String> = env::args().collect() ;
	let config = Config::new(&args) ;
		  
	println!("Searching for {}", config.query) ;
	println!("in file {}", config.filename) ;

	let contents = fs::read_to_string(config.filename).expect("Something went wrong reading the file") ;
	println!("With text: \n{}", contents) ;
}

// to link query with filename
struct Config{
	query: String,
	filename: String,
}

impl Config {
	fn new(args: &[String]) -> Config {
		if args.len() < 3 {
			panic!("not enough arguments") ;
		}
		let query = args[1].clone() ;
		let filename = args[2].clone() ;

	Config { query, filename }
	}
}
```

better way to handle errors
```rust
use std::env;
use std::fs;
use std::process; // to exit a program without panicing
use std::error::Error ;
  

fn main() {
	let args: Vec<String> = env::args().collect() ;
	let config = Config::new(&args).unwrap_or_else( |err: &str| {
	println!("Problem parsing arguments: {}", err) ;
	process::exit(1) ;
	}) ;

	println!("Searching for {}", config.query) ;
	println!("in file {}", config.filename) ;

	if let Err(e) = run(config) {
		println!("Application error: {}" , e) ;
		process::exit(1) ;
	}
}

fn run(config: Config) -> Result<(), Box<dyn Error>> {
	let contents = fs::read_to_string(config.filename)?;
	println!("With text: \n{}", contents) ;

	Ok(())
}

// to link query with filename
struct Config{
	query: String,
	filename: String,
}

impl Config {
	fn new(args: &[String]) -> Result<Config, &str> {
	if args.len() < 3 {
		return Err("not enough arguments") ;
	}

	let query = args[1].clone() ;
	let filename = args[2].clone() ;

	Ok(Config { query, filename })
	}
}
```

------
Extract some logic from the `main.rs`
a new file in `src` > `libr.rs` (a root of a lib crate) and:
- paste in it `run` function and `Config` structure
- paste some `use` (`fs`, `error`)
- make `run` and `Config` public and fields public too
- import `Config` to `main` -> `use minigrep:Config` (*minigrep* it is a name of project) -> now you can use `Config` in `main.rs`
- if you want to use `run` function in `main`, write `minigrep::run`
- 

`main.rs`
```rust
use std::env;
use std::process; // to exit a program without panicing
use minigrep::Config ;

fn main() {
	let args: Vec<String> = env::args().collect() ;
	let config = Config::new(&args).unwrap_or_else( |err: &str| {
	println!("Problem parsing arguments: {}", err) ;
	process::exit(1) ;
	}) ;

	println!("Searching for {}", config.query) ;
	println!("in file {}", config.filename) ;

	if let Err(e) = minigrep::run(config) {
		println!("Application error: {}" , e) ;
		process::exit(1) ;
	}
}
```


`lib.rs`
```rust
use std::error::Error ;
use std::fs;

pub fn run(config: Config) -> Result<(), Box<dyn Error>> {
	let contents = fs::read_to_string(config.filename)?;
	println!("With text: \n{}", contents) ;
	Ok(())
}

	// to link query with filename
pub struct Config{
	pub query: String,

	pub filename: String,
}

impl Config {
	pub fn new(args: &[String]) -> Result<Config, &str> {

	if args.len() < 3 {
		return Err("not enough arguments") ;
	}
	let query = args[1].clone() ;
	let filename = args[2].clone() ;
	Ok(Config { query, filename })
	}
}
```

---
## testing

`export CASE_INSENSITIVE=true` in linux you set a environment variable `CASE_INSENSITIVE` as `true`

`unset CASE_INSENSITIVE`

`env:var("<varName>)"` it reads a value of `varName`
`is_err()` sprawdza, czy wynik odczytu zmiennej środowiskowej zwraca błąd (jeśli  błąd, zwraca `true`, jeśli sukces, zwraca `false`)

`eprintln!` makro, które wyświetla błędy na standardowe wyjście

można przekierować terminal(standardowe wyjście) ma plik (`cargo run > output.txt`)

`cargo run to poem.txt > output.txt`  in the file will be write a result
`cargo run xxx poem.txt > output.txt` int the file will be write an error message


```rust
#[cfg(test)]
mod tests {
	use super::*;
}
```

in `lib.rs` :
```rust
use std::error::Error ;
use std::fs;
use std::env;
  

pub fn run(config: Config) -> Result<(), Box<dyn Error>> {
	let contents = fs::read_to_string(config.filename)?;
	let results = if config.case_sensitive{
		search(&config.query, &contents)
		} else {
			search_case_insensitive(&config.query, &contents)
		} ;
	for line in search(&config.query, &contents){
		println!("{}", line) ;
	}

	Ok(())
}

// to link query with filename
pub struct Config{
	pub query: String,
	pub filename: String,
	pub case_sensitive: bool,
}

impl Config {
	pub fn new(args: &[String]) -> Result<Config, &str> {
	if args.len() < 3 {
		return Err("not enough arguments") ;
	}

	let query = args[1].clone() ;
	let filename = args[2].clone() ;
	let case_sensitive = env::var("CASE_INSENSITIVE").is_err() ;

	Ok(Config { query, filename, case_sensitive })
	}
}


pub fn search<'a>(query: &str, contents: &'a str) -> Vec<&'a str>{

let mut results: Vec<&str> = Vec::new() ;

for line in contents.lines(){
	if line.contains(query){
	results.push(line) ;
		}
	}

	results
}

pub fn search_case_insensitive<'a>(
	query: &str ,
	contents: &'a str,
) -> Vec<&'a str>{

	let query: String = query.to_lowercase();
	let mut results = Vec::new();

	for line in contents.lines(){
		if line.to_lowercase().contains(&query){
			results.push(line) ;
		}
	}
	results
}


#[cfg(test)]
mod tests {
	use super::* ;

#[test]
fn case_sensitive(){

	let query = "duct";
	let contents = "\
Rust:
safe, fast, productive.
Pick three.
Duct tape.";
assert_eq!(vec!["safe, fast, productive."], search(query, contents)) ;

}

#[test]
fn case_insensitive(){
	let query: &str = "rUsT" ;
	let contents: &str = "\
Rust:
safe, fast, productive.
Pick three.
Trust me." ;

	assert_eq!(
		vec!["Rust", "Trust me."],
		search_case_insensitive(query, contents)
	)
	}
}
```

`main.rs`
```rust
use std::env;

use std::process; // to exit a program without panicing

  

use minigrep::Config ;

  

fn main() {

let args: Vec<String> = env::args().collect() ;

let config = Config::new(&args).unwrap_or_else( |err: &str| {

eprintln!("Problem parsing arguments: {}", err) ;

process::exit(1) ;

}) ;

  

println!("Searching for {}", config.query) ;

println!("in file {}", config.filename) ;

  

if let Err(e) = minigrep::run(config) {

eprintln!("Application error: {}" , e) ;

process::exit(1) ;

}

}
```


