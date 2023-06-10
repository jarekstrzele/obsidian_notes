[[_ Ultimate Rust Crash Course 1]]

>[!info] biblioteka `crossterm`
>dostarcza abstrakcji i funkcji do manipulacji terminalami na różnych platformach
>- **manipulacja terminalem** (alternatywny ekran, powrót na standardowy ekran, czyszczenie ekrany, zmiana rozmiaru, kolory, obrazki, ...)
>- **Kursor**: biblioteka umożliwia kontrolę nad kursorami w terminalu (pozycja kursora, ukrywanie kursora, pokazywanie, poruszanie, zwracanie info o położeniu kursora...)
>- **zdarzenia wejściowe** odczytywanie i interpretacja zdarzeń wejściowych z terminala 
>- **stylizacja i formatowanie tekstu**

`use crossterm::{terminal, ExecutableCommand} ;`
- moduł `terminal` zwiera finkcje i typy związane z zarządzaniem terminalem, takie jak przejście do alternatywnego ekranu ...
- moduł `ExecutableCommand` - to trait, który rozszerza  możliwości strumienia `std::io::stdout()`



