#cplusplus  #udemy #takeiteasy_academy

### `.cpp`


1970 język C Dennis Ritchi
1983 C++
1998 standard c++98
2020 stndart c++20

C++
- to język wieloparadygmatowy (proceduralne, obiektowe, generyczne(uogólnione, bez znajomości typów danych))
- to język wieloplatforomowy
- służy do tworzenie
	- gier (ArianEngine), 
	- aplikacje, 
	- bazy danych (MySQL, Postgress),
	- systemy operacyjne, grafika komputerowam chmura
	- systemy wbudowane


NARZĘDZIA
- VS Code
	- extensiont c/c++
- kompilator MinGW
	- na Win(`base-bin`, `gcc-g++-bin`)
	- win: System i zabezpieczeni, ... zmienne środowiskowe, zmienne systemowe > Path (edytujemy, nowy i wpisujemy ścieżkę dostępu)
- Debugger(c/C++ Debugger)


# RUN
## `$ g++ -o first first.cpp`
`first.cpp` to plik z kodem źródłowym

program.cpp
```c++
#include <iostream>

int main(){
	std::cout << "hello World\n" ;
	return 0 ;
}
```

`g++ -o program program.cpp`
`-o program` tak będzie nazywała się utworzona aplikacja

`program.exe` w konsoli wykonanie programu


---
# strumień wejścia / wyjścia
- `cout` wypisuje tekst zapisany w cudzysłowiu
`std::cout << "Hello" ;

- `cin` odczytuje dane z klawiatury i przypusyhe je do zmiennej
`std::cin >> liczba ;`

```c++
int main()
{
    float liczba = 3.212;
    std::cout << liczba << std::endl;
    std::cout.precision(3);
    std::cout << liczba << std::endl;

    std::cout << "enter to end";
    std::cin.get();

    return 0;
}
```


```c++
int main()
{
    int liczba;
    std::cout << "Podaj liczbe: ";
    std::cin >> liczba;
    std::cout << "Podana liczba to: " << liczba;

    return 0;
}
```

---
# Błędy kompilator



