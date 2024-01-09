#kotlin/class 
[[_ 0 Kotlin Rusz Głową]]

> Projektując z wykorzystaniem dziedziczenia, wspólny kod umieszcza się w jednej klasie, a inne, bardziej wyspecjalizowane klasy mogą po niej dziedziczyć. 
> W razie konieczności zmodyfikowania kodu trzeba to będzie zrobić tylko w jednym miejscu, a zmiany w zachowaniu zostaną uwzględnione we wszystkich klasach dziedziczących to zachowanie.


>[!info] klasa bazowa
>klasa zawierająca wspólny kod 

>[!info] klasa pochodna
>- klasa dziedzicząca z klasy bazowej
>- klasa pochodna może zawierać dodatkowe właściwości i funkcje, jak również **może przesłaniać składowe odziedziczone** po klasie bazowej
>

---
# Projektowanie hierarchii dziedziczenia

>używaj dziedziczenia, aby unikać powielania kodu w klasach pochodnych



1. **Przyjrzyj się** atrybutom i zachowaniom, które są **wspólne** dla wszystkich obiektów.

2. **Zaprojektuj klasę** bazową reprezentującą wspólne stany i zachowania
klasa bazowa `Animal`:
- właściwości:
	- `image`
	- `food`
	- `habitat` podstawowe środowisko
	- `hunger` poziom głodu
- metody:
	- `makeNoise()` wydawane odgłosy
	- `eat()` 
	- `roam()` co robi, gdy nie je i nie śpi
	- `sleep()`
klasy pochodne:
`Lion`
`Hippo`
`Lynnx`
`Fox`
`Wolf`
`Cheetah`

3. **Zdecyduj**, czy klasy pochodne mają mieć charakterystyczne dla siebie **domyślne wartości** właściwości oraz **implementacje** funkcji.
wszystkie klasy pochodne będą:
- miały swoje charakterystyczne wartości właściwości (oprócz `hunger`)
- własna implementacja `makeNoise()` oraz `eat()`


4. **Szukaj** okazji **do wyodrębniania właściwości i funkcji** poprzez znajdowanie dwóch lub większej liczby klas pochodnych mających wspólne cechy lub zachowania.
wśród klas pochodnych mamy
- 2 przedstawicieli rodziny PSOWATYCH `Canine`
- 3 przedstawicieli kotowatych `Feline`

5. Uzupełnij hierarchię klas.
nowa klasa `Feline`:
- ma własną implementację `roam()`
- klasy pochodne: `Lion`, `Cheetah`, `Lynnx`
now klasa `Canine`:
	- ma własną implementację `roam()`
	- klasy pochodne `Fox`, `Wolf`
klasa `Hippo` bez zmian, dziedziczy bezpośrednio z klasy `Animal`

>[!important] test JEST
>Czy stwierdzenie, że *typ X JEST typem Y* ma sens>?
>- Jeżeli tak, to być może mogą one wystąpić w tej samej hierarchii dziedziczenia
>- to jest test jednokierunkowy: *X jest Y*, ale *Y* nie jest *X*
>- przykład: *Czy hipopotam JEST zwierzęciem?* , tak, ale zwierzę nie musi być hipopotanem
>- działa w dowolnym miejscu drzewa dziedziczenia: A jest B, B jest C, więc też A jest C
>- `Wolf` jest `Canine`, więc `Wolf` może zrobić wszystko to samo co Canine, 
>- `Wolf` jest ``
>

>[!important] test MA
>Czy stwierdzenie, że *typ X ma/zawiera typ Y* ma sens?
>- np. *Czy kuchnia ma lodówkę?*, tak, więc obiekt klasy `Kuchnia` zwiera referencję do obiektu klasy `Lodowka`, czyli klasa `Kuchnia` ma właściwość `Lodowka`







