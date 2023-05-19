#rust #freecodecamp #youtube 
https://www.youtube.com/watch?v=MsocPEZBd-M

----
[[1 Rust Calc]]
[[2 Rust Combiner]]



--------------
`rustc` the compiler which takes your Rust code and compiles it into binary (machine readable code)
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
- kod wypisuje na ekranie argumenty przekazane do programu,
- uzywa standardowej biblioteki `std`
- `fn main()`  definicja funkcji, która jest punktem wejścia programu
- `agrs()` zwraca iterator argumentów podanych przy uruchomieniu programu
- `println()` makro słążące do wypisywania tekstu na ekranie
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












