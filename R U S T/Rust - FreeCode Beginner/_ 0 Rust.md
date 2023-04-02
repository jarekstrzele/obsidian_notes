#rust #freecodecamp #youtube 
https://www.youtube.com/watch?v=MsocPEZBd-M


`rustc` the compiler which takes your Rust code and compules it into binary (machine readable code)
`rustup` the command line utility to install and update Rust
`cargo` the Rust build system and package manager


# Build a project
### `cargo new projectName`

```rust
fn main() {

    println!("Hello, world!");

}
```

# `run` the project
### `cargo run` inside the rust project folder

or

#### `rustc ./src/main.rs`  --> generates `main.exe` 
and than 
### `./main`

# `args`

```rust
use std::env::{args, Args};

fn main() {
    let args = args();
    println!("{:?}", args);
}
```


```bash
> `cargo run` 
Args { inner: ["target\\debug\\calculator.exe"] }

```

Wyjaśnienie:
- kod ypisuje na ekranie argumenty przekazane do programu,
- uzywa standardowej biblioteki `std`
- `fn main()`  definicja funkcji, która jest punktem wejścia programu
- `agrs()` zwraca iterator argumentów podanych przy uruchomieniu programu
- `println()` makro sł€żące do wypisywania tekstu na ekranie
- ponieważ przy wywołaniu programu nie przekazano żadnych argumentów, wyświetlono nazwę programu
[[makro vs function]]

```bash
> cargo run -- freecodecamp
Args { inner: ["target\\debug\\calculator.exe", "freecodecamp"] }
```


```rust
use std::env::{args, Args};

fn main() {
    let mut args:Args = args();
    let first = args.nth(0);
    println!("{:?}", first);
}
```

`let mut args: Args = args()` 
- `mut` mutable
- `: Args` has type `Args`
- `args.nth` returns the first argument 

```bash
> `cargo run -- freecodecamp` 
Some("target\\debug\\calculator.exe")
```

#### change to:
`let first = args.nth(1)`
```bash
> cargo run -- freecodecamp
Some("freecodecamp")
```

#### change to:
`let first = args.nth(1).unwrap()`
```bash
> cargo run -- freecodecamp
"freecodecamp"
```


## `args` is an iterator
So, when it returns a value its index is changed
```rust
use std::env::{args, Args};  

fn main() {
    let mut args:Args = args();

    let first: String = args.nth(1).unwrap();
    let operator: String = args.nth(0).unwrap();
    let second: String = args.nth(0).unwrap();
    println!("{:?} {} {} ", first, operator, second);
}
```

```bash
> cargo run 1 + 2
"1" + 2 
```


## Calc first version
```rust
use std::{env::{args, Args}, result};


fn main() {
    let mut args:Args = args();
  
    let first: String = args.nth(1).unwrap() ;
    let operator: char = args.nth(0).unwrap().chars().next().unwrap() ;
    let second: String = args.nth(0).unwrap() ;
  
    let first_num: f32 = first.parse().unwrap() ;
    let second_num = second.parse::<f32>().unwrap() ;
  
    let result: f32 = operate(operator, first_num, second_num) ;
    println!("{:?} ", ouput(first_num, operator, second_num, result));

}
  

fn operate(operator: char, first_number: f32, second_number: f32) -> f32 {
    if operator == '+'
    {
        // you can user `return` but you have not
        return first_number + second_number ;
    } else if operator == '-' {
        return first_number - second_number ;
    } else if operator == '*' {
        return first_number * second_number ;
    } else if operator == '/' {
        return first_number / second_number ;
    }
    else {
        return 0.0;
    }
}

fn ouput(first_number: f32, operator: char, second_number: f32, result: f32) -> String{
    format!("{} {} {} = {}", first_number, operator, second_number, result)

}
```

```bash
> cargo run -- 11 * 2 
"11 * 2 = 22"
```

## Calc second version


















