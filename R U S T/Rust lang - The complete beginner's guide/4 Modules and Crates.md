
# Module
#rust/modules 
We can break down the functionality into different files, into different components and the unit for that breakup of functionality ==IS THE MODULE==.

## How to create a module?

You create a new file `player.rs` -- this file is a module
```rust
fn play_move(name: &str){
    println!("Playing movie {}", name) ;
}

fn plau_audio(name: &str){
    println!("Playing audio {}", name) ;
}
```
 you want to use these functions in the  `main.rs` file:
 - by default functions are restricted to that file --> transform to public `pub`

`main.rs`
```rust
mod player ;

use std::io ;

fn main() {
 player::play_move("Piła") ;
}
```

## Module inside the file `mod`
```rust
mod player ;

fn main(){
	player::play_movie("some movie") ;
	clean::perform_clean() ;
}

mod clean {
	pub fn perform_clean(){
		println("Cleaning hdd") ;
	}
}
```


----------
# Crates
#rust/crate 
>[!definition] crates
>- They are an abstraction on top of modules.
>- it is the way we structure multiple modules together inside one unit that we can perform some action


Multiple modules are grouped into a crate.
Two types:
- **binary crates*
	- when you create a new project, you get a new crate and the main component of a binary crate is that has a `main` function (it is an entry point)
- **library crates**
	- it does not have an entry point for the functionality
	- it simply provides functionality for other crates.

`cargo` is used to manage crates


new file `archive.rs`
```rust
pub mod arch {
    pub fn arch_file(name: &str){
        println("Archiving file {}", name) ;
    }
}
```

in the `main.rs`
```rust
//use crate::archive::arch::arch_file;
use crate::archive::arch::arch_file as arc; // with alias

mod archive ;

fn main() {
   // arch_file("somefile.txt") ;
   arc("some file") ;
}
```

> W Rust, używanie instrukcji `use crate::some_module;` umożliwia dostęp do elementów modułu `some_module` w danym kontekście, ale nie powoduje automatycznego importu całego modułu ani nie wprowadza wszystkich jego elementów do bieżącego zakresu.

> W języku programowania Rust, instrukcje `mod` służą do definiowania modułów, czyli logicznych jednostek strukturalnych organizujących kod. W twoim kodzie masz instrukcję `mod archive;`, co oznacza, że importujesz moduł o nazwie "archive".


## import external crates

external crate are imported into the project must be added to the `toml` file

```toml
[dependencies]
rand = "0.8.5"
```
rebuild the project `cargo build`


---
W języku Rust, instrukcje `use`, `mod` i `crate` służą do organizacji i zarządzania modułami, co pomaga w strukturyzowaniu kodu i kontrolowaniu dostępu do różnych części projektu.

1. **`use`:**    
    - `use` jest używane do importowania symboli (funkcji, struktur, typów, etc.) z innego modułu do bieżącego zakresu.
    - Przykład:
	    - `use crate::some_module::some_function;`
	    - Ta instrukcja umożliwia użycie `some_function` bez konieczności używania pełnej ścieżki do niego.
    
2. **`mod`:**    
    - `mod` jest używane do definiowania nowego modułu wewnątrz pliku lub w innym pliku.
    - Przykład:
	    - `mod some_module;`
	    - Ta instrukcja informuje kompilator, że w danym pliku istnieje moduł o nazwie `some_module`, który może zawierać różne elementy kodu.

3. **`crate`:**    
    - `crate` odnosi się do korzenia projektu Rust, czyli do samego programu lub biblioteki.
    - Przykład: `use crate::some_module::some_function;`
    - W tym kontekście `crate` jest używane, aby wskazać, że `some_module` znajduje się bezpośrednio w projekcie, nie w jakimś zagnieżdżonym module.




















