#git #udemy 

---------







--------
>[!info] plik binarny
>- plik reprezentowany w systemie `0`, `1`
>- dane zapisane w formacie binarnym (informacje zakodowane jako sekwencja bitów, a nie czysty tekst,)
>- mogą reprezentować różne typy danych (obrazy, dźwięki, filmy, ...)
>- mogą być niebezpieczne

(pracuje na notepad++)

konfiguracja
`git config --global user.name <nazwa użytkownika>`
`git config --global user.email <mejl użytkownika`

--------
>[!info] repozytorium
> to katalog, w którym system kontroli wersji trzyma całą historię projektu  `.git`

`git init` inicjalizacja  --> wewnątrz folderu z projektem :
- powstaje `.git` folder
- a folder z projektem zostaje podzielony jak gdyby na trzy części:
	- `working tree`
		- wszystko, co znajduje się wewnątrz folderu z projektem **oprócz** `.git`
		- CRUD na plikach i folderach w normalny sposób
		- przestrzeń nietrwała, nie śledzona przez gita
	- `staging area (index)` - poczekalnia 
		- to folder `.git`
		- tu kopiujesz pliki i foldery przy użyciu odpowiedniej komendy 
		- są śledzone przez gita
	- `local repository`
		- to folder `.git`
		- tu kopiujesz pliki i foldery przy użyciu odpowiedniej komendy 
		- są śledzone przez gita
		- to repo jest trwała, jak raz coś zapiszesz to nie usuniesz tak łatwo, zmiany są zapisane w postaci rewizji
		- możesz podglądać dowolne pliki z dowolnej rewizji
		- możesz przywracać plik do stanu z dowolnej rewizji









