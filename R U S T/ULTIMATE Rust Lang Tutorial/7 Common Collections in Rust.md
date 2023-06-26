[[_ LetsGetRusty Ultimate Rust Lang Tutorial]]

COLLECTIONS:
- allow you to store multiple values 
- are allocated on the heap:
	- their size is changeable

# vectors

A vector will be dropped out of the scope
```rust
fn main(){
	let a = [1,2,3];
	let v:Vec<i32> = Vec::new();
	v.push(1);
	v.push(2) ;
	v.push(3) ;
	v.push(4) ;

	{
		let v2 = vec![1,2,3];
	}

	// access to third index
	let third: &i32 = &v[2] ;

	// save access - Option
	match v.get(2){
		Some(third) => println!("the third element is {}", third),
		None => println!("THere is no third element."),
	}

}
```

```rust
fn main(){
  let mut v = vec![10,20,30,40,50] ;

  let third = &v[2] ;
  v.push(6);
  println!("the third element is {}", third) ;
}
```
this code generates an error:
```bsh
let third = &v[2] ;
  |            - immutable borrow occurs here
6 |   v.push(6);
  |   ^^^^^^^^^ mutable borrow occurs here
```
W tym kodzie zastosowano referencję (`&`) przy przypisaniu wartości trzeciego elementu wektora do zmiennej "third".

Jednak następnie dodano nowy element o wartości 6 do wektora za pomocą metody "push". Operacja ta może spowodować realokację wektora, jeśli przekroczy jego pojemność. W rezultacie, referencja "third" może wskazywać na niepoprawną lokalizację pamięci, co prowadzi do niezdefiniowanego zachowania.


# strings






# hashmaps













