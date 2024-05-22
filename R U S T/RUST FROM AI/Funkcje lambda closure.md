#rust/lambda

# Podstawy

Funkcje strzałkowe w Rust:

1. Używają pionowych kresek `|` do oznaczania parametrów.
2. Mogą mieć określony typ zwracany po strzałce `->`.
3. Mogą przechwytywać zmienne z ich zewnętrznego kontekstu.
4. Są bardzo podobne do funkcji strzałkowych w JavaScript, co ułatwia ich zrozumienie dla osób znających ten język.


```rust
fn main(){
	let add = |a: i32, b :i32| -> i32 {
		a + b
	};

	let result = add(10,20);
	println!("Result: {}", result) ;
}
```


# Funkcje strzałkowe z kontekstem
> Jedną z unikalnych cech funkcji strzałkowych w Rust jest to, że mogą przechwytywać zmienne z ich zewnętrznego kontekstu (zamknięcia), co czyni je bardzo elastycznymi.


```rust
fn main(){

	let x: i32 = 5;
	let add_to_x = |y: i32| -> i32 {
		x+y
	};

	let result = add_to_x(33);	
	println!("Add_to_x=5 (33):{}", result); // Add_to_x=5 (33):38

}
```







