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
3. **Zdecyduj**, czy klasy pochodne mają mieć charakterystyczne dla siebie **domyślne wartości** właściwości oraz **implementacje** funkcji.
4. **Szukaj** okazji **do wyodrębniania właściwości i funkcji** poprzez znajdowanie dwóch lub większej liczby klas pochodnych mających wspólne cechy lub zachowania.
5. Uzupełnij hierarchię klas.










