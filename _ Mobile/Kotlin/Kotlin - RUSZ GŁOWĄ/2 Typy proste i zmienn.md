[[_ 0 Kotlin Rusz Głową]]

Zmienna jest jak kubek - można w niej coś umieścić.

Aby utworzyć zmienną, kompilator musi znać:
- nazwę
- typ
- modyfikowalność:
	- `var` można zmienić wartość zapisaną w zmiennej,
	- `val` referencja do obiektu pozostanie w tej zmiennej na zawsze i nie będzie mogła zostać zmieniona

Kompilator potrafi jednak wywnioskować typ zmiennej na podstawie wartości, jaką tej zmiennej przypiszemy.

`var x = 5` -> kompilator utworzy obiekt `Int` o wartości `5`,
czyli zmienna `x` przechowuje **referencję** do tego obiektu.




















