
# Enum
>[!info] Enum
>- data that can be one of multiple different possibilities (each possibility is called a "variant")
>- provides information about your program to the compiler (more robust programs)

```rust
enum Direction {
	Up,
	Down,
	Left,
	Right
}

fn which_way(go: Direction){
match go {
	Direction::Up => "up",
	Direction::Down => "down",
	Direction::Left => "left",
	Direction::Right = "right"
}
}

```

```rust


```













