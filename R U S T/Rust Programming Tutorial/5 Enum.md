#rust/enum #enum 
[[_ Rust Programming Tutorial]]

[[#Type]]
[[#Methods]]


---
# Type

```rust
enum Direction {
    Up,
    Down,
    Right,
    Left
}


fn main() {
    
    let player_direction: Direction = Direction::Down ;

    match player_direction{
        Direction::Up => println!("We are heading up") ,
        Direction::Down => println!("We are going all the way down") ,
        Direction::Left => println!("Left is Right") ,
        Direction::Right => println!("Moving  towards the right! ") ,
 
    }

}
```

-----
# Methods
To define your own methods or functions on enum type.


```rust
// remove any compile warrings
#![allow(dead_code)]

enum Day {
	Mon, Tue, Wed, Thur, Fri, Sat, Sun
}

impl Day {
	fn is_weekday(&self) -> bool {

	// match self -> self jest referencją
	// i porównujemy self też z referencją
	// czyli &Day::Sat, a nie z wartością, czyli
	// Day::Sat
	match self {
		&Day::Sat | &Day::Sun => return false,
		_ => return true,
		}
	}
}
  

fn main() {
	let d = Day::Tue;
	println!("Is d a weekday {}", d.is_weekday()) ;
}
```






