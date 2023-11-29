
# Start project
1. create a project `cargo new project_name`
2. in your project folder `cargo add rocket@0.5.0-rc.4`
3. the content of `main.rs`
```rust
#[macro_use]
extern crate rocket;

#[get("/")]
fn index() -> &'static str {
    "Witaj świecie!"
}

#[launch]
fn rocket() -> _ {
    rocket::build().mount("/", routes![index])
}
```

`#[launch] fn rocket() -> _ { rocket::build().mount("/", routes![index]) }`: Jest to funkcja startowa (`#[launch]`), która konfiguruje i uruchamia serwer Rocket. Tworzy ona instancję serwera, używając metody `rocket::build()`, a następnie "montuje" trasę `"/"` na funkcję `index` za pomocą makra `routes!`. Oznacza to, że gdy serwer otrzyma żądanie na ścieżce `/`, wywoła funkcję `index` i zwróci rezultat jako odpowiedź.

NOWSZA SKŁADNIA
```rust
use rocket::get;
use rocket::routes;


#[get("/")]
fn index() -> &'static str {
    "Witaj świecie!"
}
 

#[rocket::main]
async fn main() {
    rocket::build()
        .mount("/", routes![index])
        .launch()
        .await
        .unwrap();
}
```

``#[rocket::main]`
ta funkcja jest punktem wejścia aplikacji serwerowej opartej na Rocket. Dzięki temu atrybutowi, Rust wie, że ma wywołać tę funkcję jako główny punkt startowy aplikacji.


`rocket::build()`: Rozpoczyna konfigurację nowej instancji aplikacji Rocket. Tworzy konstruktor dla aplikacji, która będzie obsługiwać serwer HTTP.

`.launch()`: Rozpoczyna działanie serwera. Uruchamia serwer HTTP z zadanymi ustawieniami i trasami.

`.await`: Jest używane, ponieważ funkcja `launch()` jest asynchroniczna, aby poczekać na jej zakończenie. W przypadku asynchronicznych operacji, `await` oczekuje na zakończenie tych operacji, zanim przejdzie dalej.

`.unwrap()`: Rozpakowuje opcjonalny wynik. W przypadku wystąpienia błędu podczas uruchamiania serwera, `unwrap()` spowoduje przerwanie programu i wypisze ewentualny komunikat o błędzie.

----
# Watch - restart serwera
### `cargo install cargo-watch`

### `cargo watch -x 'run'`
- uruchomi serwer
- śledzi zmiany w plikach źródłowych
- jeżeli zmiaany wystąpią:
	- zatrzyma serwer
	- zbuduje projekt
	- uruchomi serwer


------------
# ROUTING
Rocket obsługuje routing za pomocą metody `mount(ścieżka, funkcja)`

do poprzedniego projektu do `main.rs` dodajemy nowy routing:
```rust
#[get("/about")]

fn about() -> &'static str {
  "About"
}
 
#[rocket::main]
async fn main() {
    rocket::build()
        .mount("/", routes![index, about])
        .launch()
        .await
        .unwrap();
}
```


----------
# ZADANIE - app *lista produktów*
**Aplikacja wyświetlająca listę produktów**
Aplikacja wyświetlająca listę produktów powinna mieć następujące funkcjonalności:
- Wyświetlanie listy produktów w postaci tabeli.
- Możliwość filtrowania produktów po nazwie, kategorii lub cenie.
- Możliwość sortowania produktów po nazwie, kategorii lub cenie.






