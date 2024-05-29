[[_ 0 Rust From Beginner to Expert 2.0]]


# `struct`
#rust/struct 
>
> Structs allow us **to group** related data together
>  

```rust

struct Car{
    owner: String,
    year: u32,
    fuel_level: f32,
    price: u32,
} 


fn main() {
   
    let mut car: Car = Car {
        owner: String::from("AbC"),
        year: 2022,
        fuel_level: 0.2,
        price: 29_000,
    } ;
    
    let car_year = car.year;
    car.fuel_level = 30.0 ;
    
    // let car_owner = car.owner ; // !!! Change the ownership - String is on the heap !!!!!!
    let car_owner = car.owner.clone() ;
    println!("car year {car_year}, fuel lever {}, owner {car_owner} ", car.fuel_level) ;
    
    
    let mut new_car = Car {
        owner: "new_owner".to_string(),
        ..car // values from stack will be copy, BUT FROM HEAM will be borrowed!! 
    } ;
    
    println!("car {}, new car {}", car.owner, new_car.owner) ;
}
```
output
```
car year 2022, fuel lever 30, owner AbC 
car AbC, new car new_owner
```


# tuple and tuple struct

```rust
fn main() {
   let point_2D: (i32, i32) = (10,23);
   println!("point {:?}", point_2D) ; //point (10, 23)
   
   struct Point2d (i32, i32) ; // tuple struct - their fields are not named
   let p_2d: Point2d = Point2d(1,99) ;
 
}

```


# unit struct
it has a name but no fileds
```rust
fn main() {
 
	struct ABC;
 
}
```


















