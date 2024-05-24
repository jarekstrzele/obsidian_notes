#rust #udemy  #azam_nouman

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
2. **Alokacja pamięci**:
    
    - **Array**: Tablica jest alokowana na stosie, jeśli jej rozmiar jest znany w czasie kompilacji.
    - **Vector**: Wektor jest alokowany na stercie, co pozwala na dynamiczne zarządzanie pamięcią.
3. **Wydajność**:
    
    - **Array**: Dostęp do elementów jest bardzo szybki, ponieważ elementy są przechowywane w sposób ciągły w pamięci.
    - **Vector**: Dostęp do elementów jest również szybki, ale nieco wolniejszy niż w przypadku tablicy, ponieważ może wymagać realokacji pamięci podczas dodawania elementów.
4. **Funkcjonalność**:
    
    - **Array**: Oferuje podstawowe operacje na elementach, ale jest mniej elastyczny niż wektor.
    - **Vector**: Oferuje zaawansowane operacje, takie jak dodawanie, usuwanie elementów oraz zmiana rozmiaru.
5. **Użycie**:
    
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
























