#rust #udemy  #azam_nouman


------------

[[4 Ownership]]
[[4.1 Borrowing]]
[[5 Types]]











-------------
- `rustc --version`
- `cargo --version`
- `rustup update`


## https://play.rust-lang.org/?version=stable&mode=debug&edition=2021


# one file
VS CODE:
- `rustc fileName.rs` ->
- `./fileName` to execute the program

settings in VS Code
- format on save
- Mouse Wheel Zoom

# project
- `cargo new projectName`
- `cargo run` (in `target`>`debug` will be created a executing file)



----------
# Variable and Constants
variables are immutable by default

```rust
fn main() {
    let x: i16 = 1221;
    println!("x = {x}");
    // x = 22; // error
    
    let mut y = 21; // mutable y
    y=100;
    println!("y={y}");
}
```

---
# Primitive Data Types
`char` , `bool`, `u32`, `i32`  

### type aliasing
```rust
type Age = u8;
let peter_age: Age = 42;
```

### conversion
```rust
let a: i32 = 10 ;
let b: f64 = a as f64;
```


----
# Compound Data Types


> The colon syntax `::` in Rust  is used to access associated functions or methods on a type or module


## string
### `&str` - it is immutable
```rust
let fixed_str: &str = "Fixed length string";
```


### `String` - it is mutable
```rust
let mut felxible_str: String = String::from("This string will grow")
flexible_str.push('s') ;
```

## arrays and vectors
W Rust, `Vector` (typ `Vec`) i `Array` (typ `array` lub `[T; N]`) są dwoma różnymi typami struktur danych do przechowywania kolekcji elementów, ale różnią się one pod kilkoma względami:

1. **Rozmiar**:    
    - **Array**: Rozmiar jest stały i musi być określony w momencie kompilacji. Przykład: `[i32; 5]` oznacza tablicę pięciu elementów typu `i32`.
    - **Vector**: Rozmiar jest dynamiczny i może zmieniać się w czasie wykonywania programu. Przykład: `Vec<i32>` to wektor, który może zmieniać swój rozmiar.
    
1. **Alokacja pamięci**:
    - **Array**: Tablica jest alokowana na stosie, jeśli jej rozmiar jest znany w czasie kompilacji.
    - **Vector**: Wektor jest alokowany na stercie, co pozwala na dynamiczne zarządzanie pamięcią.

1. **Wydajność**:
    - **Array**: Dostęp do elementów jest bardzo szybki, ponieważ elementy są przechowywane w sposób ciągły w pamięci.
    - **Vector**: Dostęp do elementów jest również szybki, ale nieco wolniejszy niż w przypadku tablicy, ponieważ może wymagać realokacji pamięci podczas dodawania elementów.

1. **Funkcjonalność**:
    - **Array**: Oferuje podstawowe operacje na elementach, ale jest mniej elastyczny niż wektor.
    - **Vector**: Oferuje zaawansowane operacje, takie jak dodawanie, usuwanie elementów oraz zmiana rozmiaru.

1. **Użycie**:  
    - **Array**: Używane, gdy rozmiar jest znany z góry i nie zmienia się, np. `[1, 2, 3, 4, 5]`.
    - **Vector**: Używane, gdy potrzebna jest elastyczność w zakresie zmiany rozmiaru, np. `Vec::new()` lub `vec![1, 2, 3]`.

### array
`[<type>, numberOfElements]— they hold multiple values of the same type

```rust
fn main() {
  
  let arr1: [i32; 4] = [1,2,3,4] ;
  let n = arr1[1];
  println!("arr1 {:?}", arr1) ; // arr1 [1, 2, 3, 4]
  println!("arr1 {:#?}", arr1) ; 
  // arr1 [
 //    1,
 //    2,
  //   3,
 //    4,
  //  ]
  
  println!("n = {n}") ; //2
 
}
```


### vector
```rust
let mut vector: Vec<i32> = Vec::new();
vector.push(1);
vector.push(2);
vector.push(3);
println!("{:?}", vector); // Wyjście: [1, 2, 3]

let my_vec = vec![10,20,30] ;
println!("my vec: {:?}", my_vec) ;

```

### tuple
```rust
fn main() {
    let tuple: (&str, i32) = ("tom", 32) ;
    println!("my tuple: {:#?}", tuple) ;
}
```

### unit
```rust
fn main() {
    let my_unit: () = () ;
    println!("unit : {:?}", my_unit) ; //unit : ()
}
```


### type

```rust

fn main() {
    type book = (String, String, u32) ;// Add your code here to this line

    let book1: book = (
        String::from("Rust Programming Langauge"),
        String::from("RUST Community"),
        2010,
    );
    println!(
        "Book name: {}, Author: {}, Year {}",
        book1.0, book1.1, book1.2
    );

    let book2: book = (
        String::from("Rust by Example"),
        String::from("Steve Klabnik and Carol Nichols"),
        2015,
    );
    println!(
        "Book name: {}, Authors: {}, Year {}",
        book2.0, book2.1, book2.2
    );
}

```

## function
```rust
fn main() {
    let x = 3;
    let y = 4;
    println!(
        "The result of x+3 times y+5 is {}",
        times(add_3(x), add_5(y))
    );
}

fn add_3(x: i32) -> i32{
    
    x+3
}

fn add_5(x: i32) -> i32{
    
    x+5
}

fn times(a: i32,b: i32) -> i32{
    
    a*b
}
```

```rust
fn double(x: i32) -> i32 {
    x * 2
}

fn triple(x: i32) -> i32 {
    x * 3
}

fn main() {
    println!("Answer: {}", triple(triple(double(5)))); 
}
```


```rust
fn main() {
   println!("{:?}",multiply(10,20)) ;
   let result = basic_math(22,33);
   let (mul, add, sub) = result ;
   
   // scope block like function can have return value
   let full_name = {
       let name = "Tom" ;
       let surname = "Doe" ;
       
       format!("{name}, {surname}") // bez ;
   } ;
   println!("full name {full_name}") ;
   
}

fn multiply(a: i32, b: i32) -> i32 {
    println!("Multiplying") ;
    
    a*b //bez ;
}

fn basic_math(a: i32, b:i32) -> (i32, i32, i32){
    (a*b, a+b, a-b)
}
```


# condition
```rust

fn main() {
   
   let marks: i32 = 95 ;
   let mut grade: char = 'W' ;
   
   let g: char = if marks < 100 {
       'F'
   } else {
       'A'
   } ;
   
   println!("g: {g}") ;
   
   match marks {
       90..=100 => grade = 'A',
       80..=89  => grade = 'B',
       70..=79  => grade = 'C',
       _ => grade = 'F',
   }
   
   println!("grade: {}", grade) ;
}
```




```rust
// Problem 1:
/*
Write a program to find the difference between the square of the sum and the sum of the squares of the first N numbers.
N will be a user-defined input that your program will take.

For example, if the user enters the number 5, you should compute the square of the sum as (1 + 2 + 3 + 4 + 5)^2 = 225.
Next, compute the sum of the squares as (1^2 + 2^2 + 3^2 + 4^2 + 5^2) = (1 + 4 + 9 + 16 + 25) = 55.
Finally, calculate the difference as 225 - 55 = 170.
*/

fn main() {
    let mut n = String::new();
    std::io::stdin()
        .read_line(&mut n)
        .expect("failed to read input.");
    let n: i32 = n.trim().parse().expect("invalid input");

    let mut square_of_sum = 0;
    let mut sum_of_squares = 0;
    
    /* Complete the code after this line */ 
    for i in 1..=n{
        square_of_sum += i ;
    }
    square_of_sum = square_of_sum.pow(2) ;
    
    for i in 1..=n{
        sum_of_squares += i.pow(2) ;
    }
    println!("result {} - {} = {}", square_of_sum, sum_of_squares, square_of_sum - sum_of_squares);
    
}
```




```rust
// Problem 3:

/*
This question involves writing code to analyze the production of an assembly line in a car factory.
The assembly line has different speeds, ranging from 0 (off) to 10 (maximum).
At the lowest speed of 1, the assembly line produces a total of 221 cars per hour.
The production rate increases linearly with the speed,
meaning that a speed of 4 produces 4 * 221 = 884 cars per hour.

However, higher speeds increase the likelihood of producing faulty cars that need to be discarded.
The success rate depends on the speed, as shown in the table below:
· Speeds 1 to 4: 100% success rate.
· Speeds 5 to 8: 90% success rate.
· Speeds 9 and 10: 77% success rate.

You need to write two functions:
1. The first function, total_production(), calculates the total number of 
cars successfully produced without faults within a specified time given in hours. The function takes the number 
of hours and speed as input and returns the number of cars successfully produced.
2. The second function, cars_produced_per_minute(), calculates the number of
cars successfully produced per minute. The function takes the number of hours and speed 
as input and returns the number of cars produced per minute.
Write the code for both functions based on the provided specifications.
*/


fn main() {
    println!("{}", total_production(6, 5) as i32); // to round the values we use i32. just ignore for mow
    println!("{}", cars_produced_per_minutes(6, 5) as i32); // to round the values we use i32. just ignore for mow
}

fn total_production(hours: u8, speed: u8) -> f32 {
    let success_rate: f32;
    success_rate = match speed {
        1..=4 => 1.0,
        5..=8 => 0.9,
        9..=10 => 0.77,
        _ => 0.0
    } ;
    
    
    (hours as f32 * 221.0 * success_rate * speed as f32)
    
}

fn cars_produced_per_minutes(hours: u8, speed: u8) -> f32 {
    let success_rate: f32;
    
    success_rate = match speed {
        1..=4 => 1.0,
        5..=8 => 0.9,
        9..=10 => 0.77,
        _ => 0.0
    } ;

    println!("rate {}", success_rate) ;
    
    (hours as f32 * 221.0 * success_rate * speed as f32) / (60.0 * hours as f32)
    
}

```


```rust
// Problem 5:
// Solution:
/*
A Pythagorean triple consists of three positive integers a, b, and c, satisfying the condition a^2 + b^2 = c^2.
These triples are commonly written as (a, b, c), and a well-known example is (3, 4, 5).

Write a program that computes the Pythagorean triplet such that a < b < c and a + b + c = 1000.
*/

fn main() {
    for a in 1..=1000 {
        for b in a..=1000 - a {
            let c = 1000 - a - b;
            if a * a + b * b == c * c {
                println!("Got a triplet {:?}", (a, b, c));
            }
        }
    }
}

```


------
# Comments
#rust/comment

```rust
// inline comment

/*

multiline comments

*/
```


# print
```rust
print!("abc\n") ;
println!("abc") ;
println!(" \" double quotes \"  \\  ");

 println!("Second argument is \"text\" {1} first argument is 20 {0} ", 20, "text") ; // Second argument is "text" text first argument is 20 20 


println!("Your are {name}, you are {age} old", age=23, name="Tom");
// Your are Tom, you are 23 old


```


# read data
```rust

fn main() {
    let mut n: String = String::new();
    std::io::stdin()
        .read_line(&mut n)
        .expect("fail to read input") ;
        
    let n: f64 = n.trim().parse().expect("invalid input") ;
    println!("n={n}") ;
        
}
```

























