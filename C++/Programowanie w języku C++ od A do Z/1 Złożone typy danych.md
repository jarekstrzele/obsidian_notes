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
#include <vector>


vector <int> liczby;

vector <int> liczby {4,2,4,3} ;
```


```c++
#include <iostream>
#include <vector>

using namespace std;

int main() {
    
    // vector <int> liczby;

    vector <int> liczby {2, 3, 411, 5};
    vector <char> znaki {'a', 'e', 'i', 'o', 'u'};

    cout << liczby[2] << endl; // 411
    cout << znaki[0] << endl; // a

    znaki[0] = 'q';
    cout << znaki[0] << endl; // q

    cout << "Przed push_back: " << liczby.size() << endl; // 4
    liczby.push_back(1122);
    cout << liczby[3] << endl; // 5
    cout << liczby[4] << endl; // 1122
    cout << "Po dodaniu wartości: " <<  liczby.size() << endl; //5




    return 0;

}
```


-----
# ciągi znaków
zbiór znaków można zapisać w postaci tablic (taka tablica kończy się znakiem `null`)

```c++
char ciag[] = "Hello" ; // H e l l o \0
```





