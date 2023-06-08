[[_ 0 Uczenie maszynowe z JS]]

**uczenie maszynowe**
- wykorzystanie wielkiego zbioru danych
- prawdopodobieństwo
- statystyka
- algebra liniowa
- rachunek wektorowy

----
[[#Przetwarzenie danych]]
[[#Identyfikacja zmiennych]]
[[#Czyszczenie danych]]
[[#Transformacje]]
[[#Typy analizy]]
[[#Traktowanie brakujących danych]]
[[#Traktowanie danych odstających]]


----
# Przetwarzenie danych
**GIGO** *garbage in, garbage out* śmieci na wejściu, śmieci na wyjściu, czyli algorytm będzie tyle wart, ile warte są dane do niego wprowadzone

W uczeniu maszynowym ważną kwestią są:
- wstępne przetwarzanie  danych (to temat tego rozdziału)
- końcowe przetwarzanie danych

przykład wstępnego przetwarzania danych:
- CNN (*Convolutional Neural Networks*) konwolucyjna sieć neuronowa, splotowa sieć neuronowa
- CNN przetwarza obrazy, ale nie dowolne, lecz taki, które spełniają odpowiednie wymagania (np. kolory, rozmiar, ilość pikseli)
- jakość danych też ma znaczenie (np. 100 pacjentów, ale jeden z nich ma wzrost 221 (*element odstający*) -czy to prawdziwy wzrost, czy 100 pacjentów wystarczy, ....)




-----
## Identyfikacja cech
s.42
błędy w stosowaniu uczenia maszynowego (błędnie przetworzone dane)
- **nieistotne cechy** - uczenie maszynowe doskonale nadaje się do odnajdywania wzorców w danych, jednak nie wszystkie dane takie wzorce zawierają
- **przetrenowany model** - model potrafi doskonale przewidywać np. zachowania zakupowe Jana Kowalskiego, ale nie potrafi uogólnić wzorca do szerszego zastosowania (np. model uznał losową daną za istotną, i takie dane zostały wielokrotne przetworzone w procesie uczenie, to spowodowało błędy )

> Aby rozwiązać te problemy, musimy dokonać lepszego wyboru cech przekazywanych do modelu i wykorzystywanych w procesie uczenia

## Przekleństwo wymiarowości
- *Na przykład: algorytm, który ma dobierać reklamy dla klientów w sklepie internetowym. Jeśli dla każdego użytkownika odwiedzającego nasz sklep internetowy rejestrujemy 60 różnych miar, to pracujemy w **50-wymiarowej przestrzeni**.
- analiza o wymiarach `100x100` pikseli zapisane w skali szarości -> operujemy na przestrzeni **10 tys. wymiarów**




-------------
# Identyfikacja zmiennych


----
# Czyszczenie danych
















--------
# Transformacje










-------
# Typy analizy
















--------
# Traktowanie brakujących danych













--------
# Traktowanie danych odstających




















