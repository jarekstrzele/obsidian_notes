#kotlin #android 

zmiana koloru dla całej aplikacji
`res>values>themes>thems.xml`

```xml
<!-- Base application theme. -->  
<style name="Base.Theme.Calculator" parent="Theme.Material3.DayNight.NoActionBar">  
    <!-- Customize your light theme here. -->  
    <item name="colorPrimary">@color/grey</item>  
</style>
```
`grey` jest zdefiniowany w `res/values/colors/xml`

>Atrybut `android:layout_weight` jest używany w połączeniu z `android:layout_width="0dp"` w układach typu `LinearLayout` w celu rozdzielania dostępnej przestrzeni poziomej między elementami o równym wagom.

> Jeśli użyjesz `android:layout_width="0dp"` w połączeniu z `android:layout_weight`, oznacza to, że szerokość elementu zostanie dynamicznie dostosowana w zależności od wartości `android:layout_weight` oraz dostępnej przestrzeni na ekranie. Jeśli szerokość nie jest ustawiona na "0dp", to element będzie próbował zajmować tyle miejsca, ile jest potrzebne do wyświetlenia jego zawartości, a waga nie będzie miała wpływu na rozmiar elementu.







