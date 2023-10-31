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



