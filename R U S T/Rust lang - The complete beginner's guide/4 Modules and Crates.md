
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



















