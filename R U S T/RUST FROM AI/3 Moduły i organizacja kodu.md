

> Moduły pozwalają na dzielenie kodu na logiczne jednostki, co ułatwia utrzymanie i organizację projektu.

```rust
// Definiujemy moduł
mod greetings {
    pub fn say_hello() {
        println!("Hello, world!");
    }

    fn private_function() {
        println!("This is private.");
    }
}

fn main() {
    // Wywołujemy funkcję z publicznego modułu
    greetings::say_hello();
    // greetings::private_function(); // Błąd: funkcja jest prywatna
}

```








