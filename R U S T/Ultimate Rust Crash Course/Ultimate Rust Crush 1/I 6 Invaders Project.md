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

>o wywołanie `audio.wait()` zapewnia, że program nie zakończy się przed upewnieniem się, że wszystkie dźwięki zostały odtworzone w całości.

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





