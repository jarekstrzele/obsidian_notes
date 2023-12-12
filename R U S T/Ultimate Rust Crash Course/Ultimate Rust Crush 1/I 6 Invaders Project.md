[[_ Ultimate Rust Crash Course 1]]

>[!info] biblioteka `crossterm`
>dostarcza abstrakcji i funkcji do manipulacji terminalami na różnych platformach
>- **manipulacja terminalem** (alternatywny ekran, powrót na standardowy ekran, czyszczenie ekrany, zmiana rozmiaru, kolory, obrazki, ...)
>- **Kursor**: biblioteka umożliwia kontrolę nad kursorami w terminalu (pozycja kursora, ukrywanie kursora, pokazywanie, poruszanie, zwracanie info o położeniu kursora...)
>- **zdarzenia wejściowe** odczytywanie i interpretacja zdarzeń wejściowych z terminala 
>- **stylizacja i formatowanie tekstu**

## add dependecies
`Cargo.toml`
```toml
[dependencies]
crossterm="0.17.5"
rusty_audio = "1.1.4"
rusty_time = "0.11.0"
```

`crago build && cargo build --release`
>- So, when you run `cargo build && cargo build --release`, you are first building the project in a non-optimized mode, and then building it again in an optimized release mode.
> - This is a common practice in Rust development, where the non-optimized build is used for development and debugging, while the optimized release build is used for deploying the final version of the project.

miałem błędy na POP OS, bo brakowało paczki w systemie:
`$ sudo apt-get install libasound2-dev`



Invaders 1.0
```rust
use std::error::Error;
use rusty_audio::Audio ;

fn main() -> Result<(), Box<dyn Error>>{
	let mut audio = Audio::new() ;
	audio.add("explode", "explode.wav") ;
	audio.add("lose", "lose.wav") ;
	audio.add("move", "move.wav") ;
	audio.add("pew", "pew.wav") ;
	audio.add("startup", "startup.wav") ;
	audio.add("win", "win.wav") ;
	audio.play("startup") ;

	// CLEANUP
	audio.wait() ;
	Ok(())
}
```

> `Box<dyn Error>` oznacza, że błąd może być dowolnego typu implementującego trait `Error` z biblioteki standardowej.

> `audio.wait()` zapewnia, że program nie zakończy się przed upewnieniem się, że wszystkie dźwięki zostały odtworzone w całości.

> `Ok(())` This line returns an `Ok` value indicating successful execution of the program. The empty parameter `()` represents the absence of any error or additional data.


----

`use crossterm::{terminal, ExecutableCommand} ;`
- moduł `terminal` zwiera funkcje i typy związane z zarządzaniem terminalem, takie jak przejście do alternatywnego ekranu ...
- moduł `ExecutableCommand` - to trait, który rozszerza  możliwości strumienia `std::io::stdout()`

version 1.0
```rust
use std::{
	error::Error,
	sync::mpsc::{self, Receiver},
	time::{Duration, Instant},
	{io, thread},
};

use crossterm::{
	cursor::{Hide, Show},
	event::{self, Event, KeyCode},
	terminal::{self, EnterAlternateScreen, LeaveAlternateScreen},
	ExecutableCommand,
};

use rusty_audio::Audio;
  

fn main() -> Result<(), Box<dyn Error>>{
	let mut audio = Audio::new() ;
		audio.add("explode", "explode.wav") ;
		audio.add("lose", "lose.wav") ;
		audio.add("move", "move.wav") ;
		audio.add("pew", "pew.wav") ;
		audio.add("startup", "startup.wav") ;
		audio.add("win", "win.wav") ;
		audio.play("startup") ;

//terminal
	let mut stdout = io::stdout() ;
	terminal::enable_raw_mode()? ;
	stdout.execute(EnterAlternateScreen)?;
	stdout.execute(Hide)?;

//game loop
	'gameloop: loop {
		while event::poll(Duration::default())?{
			if let Event::Key(key_event) = event::read()?{

	match key_event.code {
		KeyCode::Esc | KeyCode::Char('q') =>{
		audio.play("lose");
		break 'gameloop;
	}
	_ =>{}
	}
	}
}
}

// CLEANUP
	audio.wait() ;
	stdout.execute(Show)? ;
	stdout.execute(LeaveAlternateScreen)? ;
	terminal::disable_raw_mode()? ;
	Ok(())
}
```

> Opis krok po kroku, co się dzieje w tym fragmencie:
>1. `gameloop: loop {` - Zaczynamy nieskończoną pętlę gry oznaczoną etykietą `'gameloop`. Etykieta ta będzie używana później, aby przerwać zagnieżdżoną pętlę.
> 2. `while event::poll(Duration::default())? {` - Wewnątrz pętli, sprawdzamy, czy są dostępne jakiekolwiek zdarzenia. Funkcja `event::poll(Duration::default())` sprawdza, czy są jakieś zdarzenia w kolejce zdarzeń. Jeśli tak, to pętla jest wykonywana. `Duration::default()` oznacza domyślny czas oczekiwania na zdarzenia.
> 3. `if let Event::Key(key_event) = event::read()? {` - Jeśli jest dostępne zdarzenie typu `Event::Key`, to rozpakowujemy `key_event` i przechodzimy do bloku instrukcji wewnątrz tego warunku. Funkcja `event::read()` odczytuje następne zdarzenie z kolejki zdarzeń.
> 4. `match key_event.code {` - Tutaj rozpoczyna się dopasowanie kodu klawisza `key_event.code` do różnych przypadków.
> 5. `KeyCode::Esc | KeyCode::Char('q') => {` - Jeśli kod klawisza jest równy `KeyCode::Esc` (klawisz Escape) lub `KeyCode::Char('q')` (klawisz 'q'), wykonujemy następujące instrukcje:
	    - `audio.play("lose");` - Odtwarzamy dźwięk "lose" przy użyciu obiektu `audio`.
	    - `break 'gameloop;` - Przerywamy nadrzędną pętlę gry oznaczoną etykietą `'gameloop`. Oznacza to, że program opuści pętlę gry i przejdzie dalej w kodzie.
    6. `_ => {}` - To jest tzw. wzorzec underscore, który pasuje do wszystkich innych przypadków, które nie zostały dopasowane wcześniej. W tym przypadku, jeśli kod klawisza nie jest równy `KeyCode::Esc` ani `KeyCode::Char('q')`, wykonujemy pustą instrukcję.
    

> Powyższy fragment kodu tworzy pętlę, która sprawdza zdarzenia w kolejce zdarzeń, odczytuje klawisze i reaguje na określone kody klawiszy. Jeśli wciśnięty zostanie klawisz Escape lub 'q', odtwarza się dźwięk "lose" i pętla gry jest

--------
# Divide the code

`pub type Frame = Vec<Vec<&'static str>>`

> W podanym fragmencie kodu definiowany jest nowy typ `Frame`, który jest aliasem dla `Vec<Vec<&'static str>>`.

> `Vec<T>` jest wektorem dynamicznej wielkości, który przechowuje elementy typu `T`. W przypadku `Frame`, jest to wektor, który przechowuje wektory elementów typu `&'static str`.

> `&'static str` jest typem odwołania do napisu (string) o statycznym czasie życia. Oznacza to, że referencja jest ważna przez cały czas trwania programu.

> Zatem `Frame` jest wektorem, który zawiera wektory odwołań do napisów o statycznym czasie życia. Może to być używane do reprezentacji dwuwymiarowej tablicy lub siatki napisów, gdzie każdy wiersz zawiera różną liczbę elementów tekstowych.

> Metoda `with_capacity` służy do utworzenia wektora z zadaną pojemnością, czyli rezerwuje pamięć na określoną liczbę elementów, ale bez faktycznego ich inicjowania. Pojemność jest informacją dla wektora, ile elementów można przechować przed koniecznością realokacji pamięci w celu zwiększenia pojemności.


`> Stdout` jest strumieniem reprezentującym standardowe wyjście (zazwyczaj terminal lub konsolę), do którego można wysyłać dane w celu wyświetlenia ich użytkownikowi.


```rust
pub fn render(stdout: &mut Stdout, last_frame: &Frame, curr_frame: &Frame, force: bool) { if force { stdout.queue(SetBackgroundColor(Color::Blue)).unwrap(); stdout.queue(Clear(ClearType::All)).unwrap(); stdout.queue(SetBackgroundColor(Color::Black)).unwrap(); stdout.queue(SetForegroundColor(Color::White)).unwrap(); }
```

Podany fragment kodu jest przykładem funkcji `render`, która przyjmuje jako argumenty:

- Referencję do mutowalnego `Stdout` (`&mut Stdout`), która umożliwia zapis do standardowego wyjścia.
- Referencje do dwóch struktur `last_frame` i `curr_frame`, które są typem `Frame`.
- Wartość logiczną `force`, która wskazuje, czy należy wymusić odświeżenie wyjścia.

Jeśli wartość `force` jest prawdziwa (`true`), następuje sekwencja poleceń wywołujących różne akcje na standardowym wyjściu, które zmieniają kolor tła, czyśćą ekran oraz ustawiają kolory czcionki. Kod wykorzystuje `stdout.queue()` do kolejkowania poleceń, które zostaną wykonane po wywołaniu metody `flush()`.

Oto krótkie wyjaśnienie poszczególnych poleceń:

- `stdout.queue(SetBackgroundColor(Color::Blue)).unwrap();` - Ustawia kolor tła na niebieski.
- `stdout.queue(Clear(ClearType::All)).unwrap();` - Czyści ekran, usuwając wszystko.
- `stdout.queue(SetBackgroundColor(Color::Black)).unwrap();` - Ponownie ustawia kolor tła na czarny.
- `stdout.queue(SetForegroundColor(Color::White)).unwrap();` - Ustawia kolor czcionki na biały.

Cała sekwencja poleceń ma na celu wykonanie pewnych operacji wizualnych na standardowym wyjściu, najprawdopodobniej w celu odświeżenia obrazu lub zmiany jego wyglądu.










