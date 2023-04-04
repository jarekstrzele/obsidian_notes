#rust #udemy #gavadinov_lyubomir


RUST IS A MODERN SYSTEMS PROGRAMMING LANGUAGE:
- memory safe
- no NULL
- no Exceptions
- modern package manager (`cargo`)
- no data races

`rustc --version` rust compiler
`cargo --version`  
`rustup --version` tool chain installer (to update compiler or cargo)

**tools**
https://www.rust-lang.org/tools

vs code extension:
- THe Rust Programmin Language
- crates

**cargo**
`cargo new project_name`

*packages*/**crates** : https://crates.io
for example: crate `rand`:
- `cargo add rand`  or
- add `rand = "0.8.5"` to `Cargo.toml` file as
```toml

[dependencies]
rand = "0.8.5"
```

to **build** project
`cargo build`

to **run** project
`cargo run` (build and run)