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

indeksy tak jak w "normalnych" tablicach
```c++

//automatycznie określa długość i dodaj e \0
char ciag[] = "Hello" ; // H e l l o \0

char ciag[9] = "Hello" ; // Hello \0 \0 \0 \0

char imie[] = { 'A', 'd', 'a', 'm', '\0'} ;

sizeof(imie) ;

```


```c++
#include <iostream>
#include <vector>

using namespace std;

int main() {
   
    //inicjalizacja
    char owoc_1[20], owoc_2[20];

    cout << "Podaj piewszy owoc: ";
    cin >> owoc_1;
    cout << "Podaj drugi owoc: ";
    cin >> owoc_2;

    cout << owoc_1 << endl << owoc_2 << endl;
    strcpy_s(owoc_1, owoc_2); // owoc_1 będzie miał wartość owoc_2
    cout << owoc_1 << endl << owoc_2 << endl;

    char imie[20];
    // imie = "Tomasz" ; generuje błąd
    strcpy_s(imie, "Tomasz");

    char user_data[199];
    strcpy_s(user_data, "Jan");
    strcat_s(user_data, "Kowalski"); //konkatenacja

   
    return 0;

}
```


```c++
char ciag[] = "Programowanie strukturalne";
    cout << ciag;
```



---
# String
#cplusplus/string

- to obiekt klasy string 
- należy dodać `#include <string>`
- ns stringach można dokonywać wielu różnych działań


```c++
//deklaracja
string nazwa_zmiennej;

//deklaracja i inicjalizacja
string nazwa = "jakiś string" ;
```








