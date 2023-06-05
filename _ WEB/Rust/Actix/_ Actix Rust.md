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












