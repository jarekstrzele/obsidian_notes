#rust/closure 
[[_ LetsGetRusty Ultimate Rust Lang Tutorial]]

>[!info] Closure
>- It is like function except that it is anonymous meaning that it doesn't have name
>- it could be stored as variable and passed around 
>- it could be passed in as input parameters to a function and  it capture a variable inside the scope in which it is defined
>

---
# without closure
```rust
use std::thread;
use std::time::Duration;

fn simulated_expensive_calculation(intensity: u32) -> u32{
	println!("calculating slowly ...") ;
	thread::sleep(Duration::from_secs(2));
	
	intensity
}
  

fn main() {
	let simulated_insensity = 10 ;
	let simulated_random_number = 7 ;

	generate_workout(simulated_insensity, simulated_random_number) ;
}

fn generate_workout(intensity: u32, random_number: u32){

	let expensive_result = simulated_expensive_calculation(intensity)

	if intensity < 25 {
		println!(
			"Today, do {} pushups!",
		expensive_result
		);

	println!(
		"Next, do {} situps!",
		expensive_result
	);
} else {

	if random_number == 3 {
		println!("Take a break today! Remember to stay hydrated!") ;
	} else {
		println!(
			"Today, run for {} minutes!",
			
			expensive_result
		) ;
	}
	}
}
```

> Metoda `thread::sleep()` to funkcja w języku Rust, która służy do wstrzymywania wykonywania programu na określony czas. Wywołuje ona pauzę w działaniu bieżącego wątku przez określony czas.
> 
> Wywołanie `thread::sleep(Duration::from_secs(2))` oznacza, że bieżący wątek zostanie zatrzymany na 2 sekundy. Jest to przydatne w przypadkach, gdy chcemy wywołać opóźnienie w programie, na przykład w celu uzyskania efektu oczekiwania lub wykonywania określonych operacji w określonym interwale czasowym.
> 
> Oto wyjaśnienie poszczególnych elementów wywołania `thread::sleep(Duration::from_secs(2))`:
> 	- `thread::sleep()` - to funkcja z modułu `thread`, która jest odpowiedzialna za wstrzymywanie wykonywania wątku.
> 	- `Duration::from_secs(2)` - to sposób utworzenia obiektu `Duration` z czasem trwania równym 2 sekund. `Duration` jest strukturą w Rust, która reprezentuje określony interwał czasowy.
> 
> Jeśli chcemy zatrzymać wątek na inną ilość czasu, można użyć innych jednostek czasu, takich jak `Duration::from_millis(500)` dla 500 milisekund lub `Duration::from_micros(10000)` dla 10 000 mikrosekund.


---
# with closure
In order to define `structs`, `enums`, or even function `parameters` that use closures we need to use **generics** and **traits bound** 




