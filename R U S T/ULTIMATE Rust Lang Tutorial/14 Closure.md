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

```rust
struct Cacher<T>
where
	T: Fn(u32) -> u32,
{
	calculation: T,
	value: Option<u32>,
}
```

> `struct Cacher<T>` to struktura w języku Rust, która jest generyczna i może przechowywać funkcje (closures) jako swoje pole.
> 
> Oto wyjaśnienie poszczególnych elementów struktury `Cacher<T>`:
> 	- `T: Fn(u32) -> u32` - jest to ogólne ograniczenie typu (generic type constraint), które mówi, że `T` musi być typem, który jest funkcją. Funkcje te muszą przyjmować argument typu `u32` i zwracać wartość typu `u32`.
> 	- `calculation: T` - jest to pole struktury `Cacher`, które przechowuje funkcję (closure). Ta funkcja będzie używana do obliczenia wartości, jeśli jest to konieczne.
> 	- `value: Option<u32>` - jest to pole struktury `Cacher`, które przechowuje wynik obliczeń. Jest to typ `Option<u32>`, co oznacza, że może zawierać wartość `Some(u32)` (konkretną wartość) lub `None` (brak wartości).
> 
> Struktura `Cacher<T>` jest używana do pamiętania wyników obliczeń funkcji dla danego argumentu. Jeśli dla danego argumentu wynik jest już obliczony, zostaje on przechowany w polu `value` i może zostać zwrócony bez ponownego obliczania. Jeśli wynik nie jest jeszcze obliczony, funkcja przechowywana w polu `calculation` jest wywoływana, a jej wynik jest przechowywany w polu `value` i zwracany.
> 
> Dzięki temu struktura `Cacher<T>` pozwala na przechowywanie wyników obliczeń i unika zbędnego ponownego wykonywania obliczeń dla tych samych argumentów, co może być przydatne w celu poprawy wydajności programu.


> `Fn` to trait (interfejs) w języku Rust, który reprezentuje typy, które można wywołać jak funkcje. Jest to jedno z trzech podobnych traitów, obok `FnMut` i `FnOnce`, które różnią się sposobem, w jaki można używać funkcji.
> 
> Oto wyjaśnienie poszczególnych traitów:
> 	- `Fn`: Reprezentuje typy, które można wywołać jak funkcje, ale nie zmieniają stanu otoczenia, w którym są używane. Oznacza to, że nie mają wpływu na zmienne zewnętrzne ani nie modyfikują żadnych innych danych w swoim otoczeniu. Są to tzw. funkcje niemutowalne.
> 	- `FnMut`: Reprezentuje typy, które można wywołać jak funkcje i mogą zmieniać stan otoczenia, w którym są używane. Mogą modyfikować zmienne zewnętrzne, ale nie są w stanie zmienić samego siebie. Są to tzw. funkcje mutowalne.
> 	- `FnOnce`: Reprezentuje typy, które można wywołać jak funkcje i które konsumują swoje otoczenie przy pierwszym wywołaniu. Oznacza to, że po wywołaniu nie można ich już ponownie wywołać. Są to tzw. funkcje konsumujące.
> 
> W przypadku struktury `Cacher<T>`, która ma ograniczenie typu `T: Fn(u32) -> u32`, oznacza to, że pole `calculation` musi być funkcją, która przyjmuje argument typu `u32` i zwraca wartość typu `u32`. Może to być funkcja niemutowalna, mutowalna lub konsumująca, pod warunkiem, że spełnia ogólny warunek ograniczenia `Fn`.
> 
> Dzięki temu ograniczeniu struktura `Cacher<T>` może przechowywać różne funkcje jako swoje pole `calculation`, pod warunkiem, że spełniają wymagania dotyczące wywoływalności i typów argumentów oraz zwracanych wartości.


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


// memoization pattern to not use multiple times `expensive_closure`
struct Cacher<T>
where
	T: Fn(u32) -> u32,
{
	calculation: T,
	value: Option<u32>,
}
  

impl<T> Cacher<T>
where
T: Fn(u32) -> u32,
{
	fn new(calculation: T) -> Cacher<T>{
		Cacher {
			calculation, //this is a closure
			value: None,
			}
}


fn value(&mut self, arg: u32) -> u32 {
	match self.value{
		Some(v) => v,
		None => {
			let v = (self.calculation)(arg) ;
			self.value = Some(v) ;
			v
		}
	}
	}
}

fn generate_workout(intensity: u32, random_number: u32){

// CLOSURE but not efficient
// let expensive_closure = |num| {
// println!("calculating slowly...") ;
// thread::sleep(Duration::from_secs(2)) ;
// num
// };

  

// efficient closure

let mut cached_result = Cacher::new( |num: u32| -> u32 {
	println!("calculating slowly...") ;
	thread::sleep(Duration::from_secs(2)) ;
	num
});

//let expensive_result = simulated_expensive_calculation(intensity)

if intensity < 25 {
	println!(
		"Today, do {} pushups!",
		cached_result.value(intensity)
	);

	println!(
		"Next, do {} situps!",
		cached_result.value(intensity)
	);
} else {
	if random_number == 3 {
	println!("Take a break today! Remember to stay hydrated!") ;
} else {
	println!(
	"Today, run for {} minutes!",
	cached_result.value(intensity)
	) ;
	}
}
}
```

