#rust/enum #enum 
[[_ Rust Programming Tutorial]]

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








