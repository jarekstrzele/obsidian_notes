

# Enum
#rust/enum 
- data that can be one of multiple different possibilities (each possibility is called a "variant")
- provides information about your program to the compiler (more robust programs)

```rust
enum Direction {
	Up,
	Down,
	Left,
	Right	
}

fn which_way(go: Direction){
	match go {
		Direction::Up=>"Up",
		Direction::Down=>"down",
		Direction::Left=>"left",
		Direction::Right=>"right",
	}
}
```

--------
# Structure
- a type that contains multiple pieces of data (all or nothing - cannot have some pieces od data and not others)
- each piece of data is called a "field"
- makes working with data easier (similar data can be grouped together)




