#cplusplus  #udemy #takeiteasy_academy

### `.cpp`
TEMATY:
[[1 Złożone typy danych]]
[[2 Operatory]]






--------------

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
# przestrzenie nazw

- służą do wybrania, które znaczenie nazwy chcemy użyć:
- zapewniamy brak konfliktów między nazwami

`A::X` oraz `B::X`

w pliku :
```c++
// dyrektywa preprocesora - włączanie treści zplików nagłówkowych do kodu źródłowego
#include <iostream>

// definiowanie zakresów lub do ułatwienia dostępu do określonych elementów przestrzeni nazw w programie
using namepsace std;

int main(){
	cout << "JEzy na wiezty " << endl;

}
```

----
# Zmienne i stałe


## zmienne
- to kontenery do przechowywania wartości
- `int  float double  char string bool`


**zmienne globalne** dostęp można uzyskaź w dowolnej części programy
```c++
int liczba;

int main(){
	return 0;
}
```

**zmienne lokalne** zdefiniowane są w funkcji lib bloku kody
```c++
int main(){
	int liczba;
	
	return 0;
}
```

```c++
#include <iostream>

using namespace std;

int liczba = 10;

int main()
{
    int liczba = 200;
    cout << liczba << endl; // ->200
    cout << ::liczba << endl; // -> 10
    

    return 0;
}
```


## stałe
są niezmienne

dwa sposoby deklarowania:
```c++
#include <iostream>
// pierwszy sposób deklaracji
#define PI 3.14

using namespace std;

int main(){
	// drugi sposób deklarowania 
	const float CAL = 2.54 ;
	
	cout << PI << endl;

	return 0;
}

```


## MODYFIKATORY
służą do zmiany właściwości zmiennej


**4 rodzaje modyfikatorów**
- `signed`
- `unsigned`
- `short`
- `long`

typy danych, które można modyfikować `int  double char`

```c++

#include <iostream>
using namespace std;

int main() {
    
    signed int liczba = -14;
    cout << "Wartość liczba: " << liczba;
    cout << "  Rozmiar: " << sizeof(liczba) << endl; // 4

    unsigned int liczba2 = 14;
    cout << "Wartość liczba: " << liczba2;
    cout << "  Rozmiar: " << sizeof(liczba2) << endl; // 4

    short int liczba3 = -14;
    cout << "Wartość liczba: " << liczba3;
    cout << "  Rozmiar: " << sizeof(liczba3) << endl; // 2


    long long int liczba4 = -14;
    cout << "Wartość liczba: " << liczba4;
    cout << "  Rozmiar: " << sizeof(liczba4) << endl; // 8

    return 0;

}

```




