#rust/casting

`main.rs`
```rust
mod my_casting; // import mdule
use my_casting::{my_cast, Day} ; // use

fn main() {
	my_cast() ;
	let today: Day = Day::Monday ;
	println!("{:?}", today) ;
	println!("Is today the weekend {}", today.is_weekend()) ;


---- output
255
9
Monday
Is today the weekend false
```

`my_casting.rs`
```rust
pub fn my_cast(){
    let int_max: u8 = u8::MAX ;
    println!("{}", int_max) ;

    let int1_u8: u8 = 5;
    let int2_u8: u8 = 4;
    let int3_u32: u32 = (int1_u8 as u32) 
                        + (int2_u8 as u32);

    println!("{int3_u32}")
}

#[derive(Debug)]
pub enum Day {
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday,
    Sunday,
}

impl Day {
    pub fn is_weekend(&self) -> bool {
        match self{
            Day::Saturday | Day::Sunday => true,
            _ => false
        }
    }
}
```









