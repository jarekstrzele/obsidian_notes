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



## `HashMap`
Kolekcja, która przechowuje pary klucz-wartość.
**Klucze** są unikalne i nie mogą być zmienione.
**Wartości** 



