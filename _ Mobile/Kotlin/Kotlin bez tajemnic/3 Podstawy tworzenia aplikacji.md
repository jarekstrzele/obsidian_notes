[[_ Kotlin bez tajemnic]]

# Android Studio 
- `File>Settings>Plugin`:
	- rainbow brackets
	- nyan progress bar


# Activity and lifecycle

- `: AppCompatActivity()` dziedziczenie po tej klasie sprawia, że dana klasa jest `activity`
- definicja startowej aktywności  oraz wszystkie pozostałe aktywności w `AndroidManifest`

```xml
<activity  
    android:name=".MainActivity"  
    android:exported="true"  
    android:screenOrientation="portrait">  
    <intent-filter>  
        <action android:name="android.intent.action.MAIN" />  
  
        <category android:name="android.intent.category.LAUNCHER" />  
    </intent-filter>  
</activity>
```

- aktywności należy dzielić na fragmenty, a nie tworzyć nowe aktywności
- 


# Fragment
- reprezentują zachowanie lub część interfejsu aktywności 
- nie może istnieć fragment bez aktywności, ale aktywność może istnieć bez fragmentu
- posiadają własny widok, ale ich cykl życia zależny jest od aktywności
- są modularne
- można je wielokrotnie wykorzystywać

>[!definition] Fragmenty w Androidzie
> są częściami interfejsu użytkownika lub zachowania aplikacji, które można zintegrować w aktywność, pozwalając na bardziej modułową i wielokrotnego użytku konstrukcję interfejsu.
> Oto kilka kluczowych informacji o fragmentach w Androidzie:
>	1. **Modułowość**: Fragmenty pozwalają deweloperom podzielić interfejs użytkownika na niezależne, wielokrotnego użytku komponenty, co ułatwia zarządzanie i ponowne wykorzystanie kodu.
>	2. **Łatwa integracja**: Fragmenty mogą być łatwo zintegrowane wewnątrz aktywności, co pozwala na elastyczne zarządzanie interfejsami użytkownika w zależności od wielkości ekranu, orientacji urządzenia itp.
>	3. **Cykl życia**: Fragmenty posiadają swój własny cykl życia, co oznacza, że posiadają metody takie jak `onCreate()`, `onStart()`, `onPause()`, `onStop()`, `onDestroy()`, które odpowiadają za zarządzanie ich stanem.
>	4. **Komunikacja między fragmentami**: Fragmenty mogą komunikować się ze sobą poprzez aktywność, co pozwala na wymianę danych i interakcję pomiędzy nimi.
    
5. **Obsługa wielu ekranów**: Fragmenty są używane do tworzenia aplikacji, które mogą dostosowywać swój interfejs użytkownika do różnych rozmiarów ekranów urządzeń.

