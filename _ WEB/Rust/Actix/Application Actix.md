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

}
```







