#android/intention 

>[!info] intencja
>- to rodzaj komunikatu
>- zawsze, gdy chcemy uruchomić jedną aktywność z poziomu innej aktywności, musimy w tym celu użyć **intencji**
>- jeśli jedna aktywność chce uruchomić drugą, robi to, przesyłając do systemu Android odpowiednią intencję.
>

```kotlin
val intent = Intent(this, KlasaDocelowa::class.java)

```


