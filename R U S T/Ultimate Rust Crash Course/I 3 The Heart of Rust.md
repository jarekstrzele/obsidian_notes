[[_ Ultimate Rust Crash Course]]


# Ownership

### THREE RULES:
1. Each value has an owner.
2. Only one owner. (no variables may share ownership, other variables can borrow ownership)
3. Value gets dropped if its owner goes out of the scope

```rust
let s1 = String::from("abc") ;
le s2 = s1 ; // the value of s1 is MOVED to s2, because only one variable can own the value

```





---
# References and Borrowing




















