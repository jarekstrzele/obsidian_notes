
**1. Sprawdź, czy ciąg znaków jest liczbą:**

```kotlin
val regex = Regex("[0-9]+")

val str1 = "12345"
val str2 = "abc123"

println(regex.matches(str1)) // true
println(regex.matches(str2)) // false

```




















**Sprawdź, czy hasło ma co najmniej 8 znaków, w tym jedną dużą literę i jedną cyfrę:**
```kotlin
val regex = Regex("^(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9]).{8,}$")

val password1 = "Haslo123"
val password2 = "haslo123"

println(regex.matches(password1)) // true
println(regex.matches(password2)) // false

```
