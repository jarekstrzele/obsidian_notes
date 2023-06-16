

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

```rust
struct ShippingBox{
	depth: i32,
	width: i32,
	height: i32
}

let my_box = ShippingBox {
	depth: 3,
	width: 2,
	height: 5,
}

let tall = my_box.height ;
println!("the box is {:?} units tall", tall) ;
```


-----
# Tuples
#rust/tuple 
- a type of "record"
- store data anonymously (no need to name fields)
- useful to return pairs of data from functions
- can be "destructed" easily into variables

```rust
enum Access {
  Full,
}

fn one_two_three() -> (i32,i32,i32){
   (1,2,3)
}

let numbers = one_two_three();
let (x,y,z) = one_two_three() ;

println!("{:?}, {:?}", x, numbers.0) ; //1
println!("{:?}, {:?}", y, numbers.1) ; //2
println!("{:?}, {:?}", z, numbers.2) ; //3

let (employee, access) = ("Jake", Access::Full)




```

----------
# `impl`

```rust
struct Temperature {
	degrees_f: f64,
}

impl Temperature {
	fn freezing() -> Self {
		Self { degrees_f: 32.0 }
	}

	fn show_temp(&self){
		println!("{:?} degrees F", self.degrees_f) ;
	}
}

fn main(){
	let hot = Temperature { degrees_f: 99.9} ;
	hot.show_temp() ;

	let cold = Temperature::freezing() ;
	cold.show_temp();
}
```


```rust
struct Color{
	Browm,
	Red,
}

impl Color{
	fn print(&self){
		match self{
			Color::Brown => println!("brown"),
			Color::Red => println!("red"),
		}
	}
}

struct Dimensions{
	width: f64,
	height: f64,
	depth: f64,
}

impl Dimensions{
	fn print(&self){
		println!("width {:?}", self.width) ;
		println!("height {:?}", self.height) ;
		println!("depth {:?}", self.depth) ;
	}
}



struct ShippingBox{
	color: Color,
	weight: f64,
	dimensions: Dimensions,
}

impl ShippingBox{
	fn new(weight: f64, color: Color, dimensions: Dimensions) -> Self {
		Self {
		// because names are the same
		// you don't have to write
		// color:color, weight:weight, 
		// dimensions: dimensons
			weight,
			color,
			dimensions
		}
	}
	fn print(&self){
		self.color.print();
		self.dimensions.print();
		println!("{:?}", self,weight) ;
	}
}

fn main(){
	let small_dimensions = Dimensions {
		width: 1.0,
		height: 2.0,
		depth: 3.0,
	};
let small_box = ShippingBox::new(5.0, Color::Red, small_dimensions)



}
```












