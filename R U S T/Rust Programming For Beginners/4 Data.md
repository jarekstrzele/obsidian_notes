[[#Enum]]
[[#Struct]]
[[#Tuple]]


----
# Enum
#rust/enum 
>[!info] Enum
>- data that can be one of multiple different possibilities (each possibility is called a "variant")
>- provides information about your program to the compiler (more robust programs)
>- Enums can only be one variant at a time
>- Make program code easier to read

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
enum Direction{
  Left,
  Right,
}
  
fn main(){
  let go = Direction::Left ;

  match go {
    Direction::Left => println!("Lefft"),
    Direction::Right => println!("RRight"),
  }
}
```

```rust
enum Color{
  Blue,
  Green,
  Yellow
}
  
fn main(){
  let go = Color::Yellow ;
  print_color(go) ;
  
 
}

fn print_color(my_color: Color){
  match my_color {
    Color::Blue => println!("Blue"),
    Color::Yellow => println!("Yellow"),
    Color::Green => println!("Green"),
  }
}
```

---------
# Struct
#rust/struct

>[!info] Struct
>A type that contains multiple pieces of data
>	- all or nothin - cannot have some pieces of data and not others
>	-  each piece of data is called a "field"
>Makes working with data easier (similar data can be grouped together)


```rust
struct ShippingBox{
	depth: i32,
	width: i32,
	height: i32,
}

let my_box = ShippingBox{
	depth: 3,
	width: 2,
	height: 5,
};

let tall = my_box.height ;
println!("The box is {:?} units tall", tall) ;

```




-----
# Tuple
#rust/tuple









