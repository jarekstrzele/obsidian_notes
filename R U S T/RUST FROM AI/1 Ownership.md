
**Ownership**
>-  Każda wartość  ma jednego właściciela/zmienną, która jest odpowiedzialna za czas życia tej wartości.
>- gdy właściciel wychodzi poza zakres swojego działania, wartość jest automatycznie usunięta


**Borrowing**
>- watość poże być pożyczona przez inne zmienne
>- pożyczanie jest kontrolowane przez *wskaźniki*:
>	- `&` referencja  niezmieniająca
>			   pozwala na dostęp  do wartości bez możliwości jej zmiany
>	- `&mut` referencja niezmieniająca 
>				pozwala na modyfikację wartości


**Przykład**
W tym przykładzie, po wywołaniu funkcji `take`, wektor `v` jest przekazywany do funkcji i staje się jej "właścicielem". Po zakończeniu funkcji `take`, wektor jest zwalniany, więc próba użycia `v` w funkcji `main` kończy się błędem kompilacji. Właśnie tak działa mechanizm własności w Rust.

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




