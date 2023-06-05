#actix #rust
https://actix.rs/docs/

Actix Web lets you quickly and confidently develop web services in Rust.
You need rust 1.59 or more.
`rustc --version`


# *Hello World* App
```rust
cargo new hello-world
cd hello-word
```

Cargo.toml
```toml
[dependecies]
actix-web ="4"
```

> An application developed with Actix Web will expose an HTTP server contained within a native executable. 
> You can either put this behind another HTTP server like nginx or serve it up as-is. 
> Even in the complete absence of another HTTP server Actix Web is powerful enough to provide HTTP/1 and HTTP/2 support as well as TLS (HTTPS). This makes it useful for building small services ready for production.

### request
- **request handlers** use async functions that accept zero or more parameters
- these parameters can be extracted from a request (`FromRequest`  trait) and 
- returns a type that can be converted into an `HttpResponse` (`Responder` trait)

#### `App` 
- główny komponent, który służy do konfigurowania aplikacji serwera HTTP
- jego struktura reprezentuje aplikację serwera HTTP i jest używana do definiowania tras (routing) oraz konfiguracji obsługi żądań
- umożliwia definiowanie ścieżek URL i przypisywania im funkcje obsługi *handler* (funkcja wywoływana w momencie otrzymania żądania)
- przykładowe metody:
	- `route()` umożliwia zdefiniowanie konkretnejścieżki URL i metody HTTP, która ma być obsługiwana przez określony handler
	- `service()` rejestruje *handler* jako obsługę okreśłonej ścieżki URL. Można zarejestrować wielokrotnie różne handlery dla tej samej ścieżki, obsługujące różne metody HTTP
	- `data()` przechowuje dane aplikacji,  które b
```rust
use actix_web::{get,post, web, App, HttpResponse, HttpServer, Responder} ;
  

#[get("/")]
async fn hello() -> impl Responder {
	HttpResponse::Ok().body("Hello world!")
}

#[post("/echo")]
async fn echo(req_body: String) -> impl Responder {
	HttpResponse::Ok().body(req_body)
}

async fn manual_hello() -> impl Responder{
	HttpResponse::Ok().body("Hey there!")
}

#[actix_web::main]
async fn main() -> std::io::Result<()>{
	HttpServer::new(|| {
		App::new()
		.service(hello)
		.service(echo)
		.route("/hey", web::get().to(manual_hello))
})
.bind(("127.0.0.1", 8080))?
.run()
.await

}
```

- `#[actix_web::main]` atrybut wskazuje, że jest to punkt wejścia dla frameworka Actix Web i rozpoczyna wykonanie serwera
- `HttpServer::new()` tworzy server HTTP i przyjmuje dwa argumenty:
- *closure*  `||`  (akurat bez argumentów) jest wykonywany w momencie tworzenia instancji serwera 
	- przekazuje konfigurację dla serwera HTTP (routing i obsługa zdarzeń)
	- zwraca obiekt typu  `App`
- *konfiguracja adresu i portu* 
	- funkcja `bind()` zwraca wynik w postaci `Result` (operator `?` do obsługi błędów)
	- jeżeli `bind()` zakończy się sukcesem, to wywoływana jest metoda `run()`
		- `run().await` - oznacza, że bieżąca funkcja `main` będzie wstrzymywana  do mementu zakończenia działania metody `.run()`







