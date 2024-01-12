#kotlin/runnable
[[Handler]]

## RUNNABLE to interfejs.

> Obiekt `Runnable` w języku Kotlin jest interfejsem, który reprezentuje kod, który może być wykonywany w tle. 
> 
> Obiekt `Runnable` jest wykorzystywany przez klasy takie jak `Handler` do wykonywania zadań w tle na wątkach innych niż główny.

## RUNNABLE ma jedną metodę
`fun run()`

> Metoda `run()` jest wywoływana, gdy obiekt `Runnable` jest przekazywany do klasy takiej jak `Handler`. Metoda `run()` może zawierać dowolny kod, który chcesz wykonać w tle.



Obiekty `Runnable` mogą być używane do wykonywania dowolnego kodu w tle. Na przykład, można je wykorzystać do:

- Wykonywania zadań, które zajmują dużo czasu, takich jak kompresowanie plików lub obliczanie dużych sum.
- Wykonywania zadań, które mogą zakłócać interfejs użytkownika, takich jak pobieranie danych z Internetu.
- Wykonywania zadań, które są wykonywane cyklicznie, takich jak aktualizacja stanu aplikacji.





