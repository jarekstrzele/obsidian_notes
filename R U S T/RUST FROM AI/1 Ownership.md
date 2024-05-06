
# **Ownership**
>-  Każda wartość  ma jednego właściciela/zmienną, która jest odpowiedzialna za czas życia tej wartości.
>- gdy właściciel wychodzi poza zakres swojego działania, wartość jest automatycznie usunięta


# **Borrowing**
>- watość poże być pożyczona przez inne zmienne
>- pożyczanie jest kontrolowane przez *wskaźniki*:
>	- `&` referencja  niezmieniająca
>			   pozwala na dostęp  do wartości bez możliwości jej zmiany
>	- `&mut` referencja niezmieniająca 
>				pozwala na modyfikację wartości


# **Przykład**
W tym przykładzie, po wywołaniu funkcji `take`, wektor `v` jest przekazywany do funkcji i staje się jej "właścicielem". Po zakończeniu funkcji `take`, wektor jest zwalniany, więc próba użycia `v` w funkcji `main` kończy się błędem kompilacji. Właśnie tak działa mechanizm własności w Rust.


## przez przekazanie
```rust
fn take(vec: Vec<i32>){

}


fn main(){
	println!("Cześć");
	let v= vec![1,2,3];
	take(v);
	println!("{:?}", v);
}
```


## przez referencję `&`
```rust
fn borrow(myvector: &Vec<i32>){
}

fn main() {

	let v = vec![1, 2, 3];
	borrow(&v);
	println!("{:?}", v); // Działa poprawnie, `v` nadal istnieje
}
```


### pętla for
```rust
for i in 10..15{

	println!("{}", i);

}

println!("--------- z = ----------");

for i in 10..=15{

	println!("{}", i);

}
```

### iterowanie po wektorze - zadanie
> napisz prostą funkcję w Rust, która przyjmuje wektor liczb całkowitych jako parametr (poprzez **pożyczenie**) i wypisuje każdy element tego wektora. Możesz użyć pętli `for` do iteracji przez elementy wektora.

```rust
fn showElems(myVector: &Vec<i32>){

	for elem in myVector{
		println!("{}", elem);
	}
}


fn main() {

	let v = vec![11,22,33,44];
	showElems(&v);
}
```

**użycie wycinka**
> Wycinki są bardziej uniwersalne i mogą być używane z różnymi rodzajami kontenerów danych, nie tylko z `Vec`.







