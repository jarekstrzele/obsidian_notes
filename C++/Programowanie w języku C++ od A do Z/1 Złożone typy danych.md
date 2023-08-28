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


# tablica wielowymiarowa

```c++
int tab[3][4] = {4,5,3,4,
				 5,2,1,2,
				 5,2,3,1} ;
```

```c++
#include <iostream>
using namespace std;

int main() {
    int tab[3][4] = { 4,5,3,4,
                      5,2,1,2,
                      5,2,30,1 };

    cout << tab[2][2]; // 30

    return 0;
}
```

```c++
 int tab[6][2] = { 4,5,
                      3,4,
                      5,2,
                      1,2,
                      5,2,
                      30,1 };
```


---

# Wektory
- to kontenery przechowujące wiele wartości tego samego typu
- jak tablice, ale rozmiar wektorów może się zmieniać dynamicznie


```c++

vector <int> liczby;

vector <int> liczby {4,2,4,3} ;
```






