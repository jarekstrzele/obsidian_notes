#android/objectoutputstream

[[16 ToDoApp]]
[[FileOutputStream]]

**ObjectOutputStream**:

- `ObjectOutputStream` jest strumieniem wyjściowym wyższego poziomu, który opakowuje `FileOutputStream`. Jego główną funkcją jest serializowanie obiektów, czyli przekształcanie ich do formatu bajtowego, który można zapisać do pliku.
- `ObjectOutputStream` potrafi serializować (czyli zamieniać na ciąg bajtów) całe obiekty, włącznie z ich strukturą i danymi, co umożliwia późniejsze ich odtworzenie w dokładnie tej samej postaci (deserializacja).

```kotlin
val fos: FileOutputStream = context.openFileOutput("example.obj", Context.MODE_PRIVATE)
val oos = ObjectOutputStream(fos)
val data = arrayListOf("Hello", "World")
oos.writeObject(data)
oos.close()
fos.close()

```


