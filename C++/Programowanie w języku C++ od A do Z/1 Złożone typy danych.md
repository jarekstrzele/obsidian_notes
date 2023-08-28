#cplusplus  #tablica #wektor #string 
[[_ 0 Programowanie w języku C++]]




-----

# tablica jednowymiarowa
zmienna, która może przechowywać wiele wartości tego samego typu

```c++

int oceny[6] ; //deklaracja
// typ_danych nazwa[rozmiar]

int oceny[6] = {4,3,2,5,5,4} ; //deklaracja i inicjalizacja
// indeks od 0

```

```c++
#include <iostream>
using namespace std;

int main() {
    
    int oceny[6] = { 4,3,2,5,5,3 };

    cout << oceny[0] << endl;
    cout << oceny[3] << endl;


    return 0;

}
```








