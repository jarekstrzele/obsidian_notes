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
// output: Args { inner: ["target\\debug\\calculator.exe"] }

```

Wyjaśnienie:
- kod ypisuje na ekranie argumenty przekazane do programu,
- uzywa standardowej biblioteki `std`
- `fn main()`  definicja funkcji, która jest punktem wejścia programu
- `agrs()` zwraca iterator argumentów podanych przy uruchomieniu programu
- `println()` makro sł€żące do wypisywania tekstu na ekranie
- ponieważ przy wywołaniu programu nie przekazano żadnych argumentów, wyświetlono nazwę programu
[[makro vs function]]









