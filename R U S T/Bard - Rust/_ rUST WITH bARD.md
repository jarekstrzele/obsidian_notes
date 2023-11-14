#bard  #rust 


# Pojęcia podstawowe

- **Kompilator:** Program, który przekształca kod źródłowy w kod maszynowy.
- **Moduł:** Jednostka kodu Rust, która może być importowana do innych modułów.
- **Funkcja:** Jednostka kodu Rust, która wykonuje określoną pracę.
- **Typ danych:** Definiuje rodzaj danych, które można przechowywać w zmiennej.
- **Instrukcja:** Jednostka kodu Rust, która wykonuje określoną operację.


# Pierwszy program

first.rs
```rust
fn main(){

    println!("Hello world") ;

}
```

aby uruchomić
```bash
> rustc first.rs
> ./first


```

## funkcja
```rust
fn add_two_numers(a : i32, b : i32) -> i32 {
    a+b
}

fn main(){
    println!("Hello world") ;
    println!("{:}", add_two_numers(11,22))
}
```


# zmienne
deklaracja zmiennej
```rust
let x : i32 = 20
```

>[!def] **Wyrażenia**
   Wyrażenie to fragment kodu, który oblicza wartość. Wyrażenia mogą zawierać zmienne, operatory i funkcje.


# pętla
`while`, `for`

```rust
fn main(){
    for i in 0..10 {
        println!("i={}", i) ;
    }
}
```




# Kolekcje
>[!info] Kolekcje
> to typy danych, które pozwalają przechować wiele elemenótw

## `Vec` tablice dynamiczne
To kolekcja, która przechowuje elementy w tablicy dynamicznej. Elementy są indeksowane od 0

  
> Funkcja "new()" wywołana na typie "Vec" tworzy nowy, pusty wektor.
> 
```rust
fn main(){
    let mut nums = Vec::new() ;
    nums.push(10) ;
    nums.push(20) ;
    nums.push(30) ;

    println!("The first number is: {}", nums[0]) ;
	println!("{:?}", nums) ;
  
}
```



## `String`
Kolekcja przechowująca ciąg znaków (indeksowane od 0)
```rust
fn main(){
    let mut name = String::new();
    name.push('A') ;
    name.push('n') ;
    name.push('t') ;

    println!("My name is {}", name) ;

}
```

```rust
fn main(){

    let mut name = String::new(); //type String
    name = "Jarosław Strzelecki".to_string() ; // convert a string litteral to String type
    println!("My name is {}", name) ;

}
```
when you declare a variable with the `let`, the type of the variable is determined by the initial value you assign to it, so better way:
```rust
fn main(){
    let name = "Jarosław Strzelecki".to_string() ;
    println!("My name is {}", name) ;
}
```

## `HashMap`
Kolekcja, która przechowuje pary klucz-wartość.
**Klucze** są unikalne i nie mogą być zmienione.
**Wartości** mogą być dowolnego typu.

```rust
use std::collections::HashMap;

fn main(){
    let mut scores = HashMap::new();
    scores.insert("John Doe", 100) ;
    scores.insert("janek kowalski", 90) ;
    println!("JD's score is: {}, JK's score is: {}", scores["John Doe"], scores["janek kowalski"]) ;
}
```

`use` it is used to bring external items into the current scope, so you canuse them without needing to fully qualify their names
`std` standard module
`collections` submodule

----------
# Struktury

>[!definition] struktury danych
>to typy danych złożone, które moga przechowywać wiele elementów
>umożliwiają organizowanie danych w sposób  logiczny


## `struct`
```rust
struct Person {
  name: String,
  age: i32,
}


fn main() {
 let john = Person{
   name:"Tom".to_string(),
   age: 34,
 };

  println!("{}",john.name);
  println!("{}",john.age);
}
```


## `enum`
```rust
enum Color{
	Red,
	Green,
	Blue,
}
```

```rust
enum Color{
    Red,
    Green,
    Blue,
}
fn main() {
 
    let color = Color::Green;
    
    match color {
        Color::Red => println!("Kolor czerwony"),
        Color::Green => println!("Kolor zielony"),
        Color::Blue => println!("Kolor niebieski"),
        _ => println!("Nothing"),
    }
    
    
    
}
```

--------
# Funkcje anonimowe

>[!info] funkcje anonimowe/domknięcia/*closures*
>- funkcje bez nazwy
>- wykonują krótkie zadania
>- mogą być przekazytwane jako argumenty do innej funkcji
>- mogą przechwytywać swoje środowisko (zamknięcie/*closure*)

**closure** przechwycenie zmiennej oznacza, że zamknęcie będzie miało dostęp do jej wartości nawet po opuszczeniu swojego pierwotnego zakresu

```rust
fn main() {
    let plus_one = |x:i32| x + 1;
    println!("3 plus 1 = {}",  plus_one(3)) ;
}
```

### ` | parametry| { kod }`


## funkcja anonimowa jako krótkie zadanie
```rust
fn main() {
 
    let mut nums = vec![1,2,3,2,4,5];
    nums.sort_by(|a, b| b.cmp(a)) ;
    println!("{:?}", nums)
}
```


## funkcja anonimowa jako argument

```rust
fn my_map<T,F>(numbers: Vec<T>, f: F) -> Vec<T>
where
    F: Fn(T) -> T,
{
    let mut result = vec![];
    
    for number in numbers {
        result.push(f(number))
    }
    
    result
}


fn main() {
 
    let mut nums = vec![1,2,3,2,4,5];
    let doubled = my_map(nums, |x| x*2) ;
    println!("{:?}", doubled) ;
    
}
```


> `where F: Fn(T) -> T`
> - Używa klauzuli `where`, aby nałożyć ograniczenie na typ `F`.
> - `F` musi być funkcją, która przyjmuje argument typu `T` i zwraca wartość tego samego typu.



> W języku Rust, `<T, F>` oznacza parametryzowany typ generyczny. Są to tzw. "generyczne typy" lub "typy parametryzowane", które pozwalają na tworzenie funkcji czy struktur danych, które mogą działać na różnych typach danych.


---------
# Kontrola przepływu
```rust
if condition {

} else {

}
```

## `if let`
`if let` pozwala na przypisanie wartości zmiennej, jeśli warunek jest spełniony.

```rust
fn main() {
    let number = Some(10);

    if let Some(number) = number {
        println!("Liczba to: {}", number);
    }
}

```

```rust
fn main() {
    let number = 10;

    match number {
        1 => println!("Liczba to 1"),
        2 => println!("Liczba to 2"),
        _ => println!("Liczba jest inna"),
    }
}
```