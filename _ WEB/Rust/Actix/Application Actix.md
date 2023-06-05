[[_ Actix Rust]]

All `actix-web` servers are built around the `App` instance:
https://docs.rs/actix-web/4.3.1/actix_web/struct.App.html

- is used for registering routes  for resources and [[middleware]] 
- stores application state shared across all handlers within the same scope
- https://docs.rs/actix-web/4.3.1/actix_web/struct.Scope.html - SCOPE - is a namespace for all routes
	- for application with scope `/app` any request with the path `/app`, `/app/`, `/app/test` would match
	- the path `/application` would not match

```rust
async fn index() -> impl Responder{
	"Hello world!"
}

#[actix_web::main]
async fn main() -> std::io::Result<()>{
	HttpServer::new(|| {
		App::new().service(
		//prefix all resources and routes attached to it ...
		web::scope("/app")
			// ... so this handles requests for '`get /app/index.html`'
			.route("/index.html", web::get().to(index))
		)
	})
	.bind(("127.0.0.1", 8080))?
	.run()
	.await
}
```

# State
- app state is shared with all routes and resources within the same scope
- state can be accessed with the `web::Data<T>`

```rust
use actix_web::{get, web, App, HttpServer} ;

//this struct represents state
struct AppState {
	app_name: String,
}

#[get("/")]
async fn index(data: web::Data<AppState>) -> String {
	let app_name = &data.app_name ; // get app_name
	format!("Hello {app_name}") // response with app_name
}

#[actix_web::main]
async fn main() -> std::io::Result<()>{
	HttpServer::new( || {
		App::new()
			.app_data(web::Data::new(AppState {
				app_name: String::from ("Actix Web"),
		}))
			.service(index)
	})
	.bind(("127.0.0.1", 8080))?
	.run()
	.await
}
```

`service(index)` rejestruje funkcję obsługującą `index` jako usługę serwera

