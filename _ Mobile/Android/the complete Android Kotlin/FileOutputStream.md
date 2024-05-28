#android/fileoutputstream

[[16 ToDoApp]]
[[ObjectOutputStream]]

**FileOutputStream**:

- `FileOutputStream` jest podstawowym strumieniem wyjściowym, który umożliwia zapis bajtów bezpośrednio do pliku. Innymi słowy, obsługuje on zapis danych w surowym formacie bajtowym.
- `FileOutputStream` sam w sobie nie ma możliwości serializowania obiektów w Javie/Kotlinie. Może tylko zapisywać surowe bajty.

Przykład użycia `FileOutputStream` do zapisu surowych bajtów:
```kotlin
val fos: FileOutputStream = context.openFileOutput("example.txt", Context.MODE_PRIVATE)
fos.write("Hello, World!".toByteArray())
fos.close()

```








