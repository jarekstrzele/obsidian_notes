[[_ the complete Android Kotlin]]

----
[[#A new project]]
[[#Virtualisation]]
[[#Installing the Genymotion Emulator]]
[[#Gradle Build System]]



----

# A new project


A NEW PROJECT -- ==wait until your project will be finished==
- verify: the emulator technology is active?
	- Task manager > Performance tab (Virtualisation: Enabled)
	- https://developer.android.com/studio/run/emulator-acceleration
- start a virtual device
	- on the top there is a phone icon (*Device Manager*/ *AVD Manager*) or from *Tools*
		- or Android SDK (Android 11.0) ; choose with *play* icon
- if you have no *res/activity_main.xml*, to 
	- samodzielnie w `res` Directory `layout` > *new* -> *layout resource file* add the name `activity_main`
	- or *File* > *Invalidate Caches / Restart*


Aby połączyć plik [activity_main.xml](https://www.google.com/search?q=activity_main.xml) z plikiem [MainActivity.kt](https://www.google.com/search?q=MainActivity.kt) w [Android Studio](https://www.google.com/search?q=Android%20Studio), wykonaj poniższe kroki:

1. Otwórz plik [MainActivity.kt](https://www.google.com/search?q=MainActivity.kt) w [Android Studio](https://www.google.com/search?q=Android%20Studio).
    
2. Znajdź metodę [onCreate](https://www.google.com/search?q=onCreate) w pliku [MainActivity.kt](https://www.google.com/search?q=MainActivity.kt). Jest to metoda, która jest wywoływana podczas tworzenia aktywności.
    
3. Wewnątrz metody [onCreate](https://www.google.com/search?q=onCreate), dodaj następującą linię kodu:
    

kotlin

setContentView(R.layout.activity_main)

Ta linia kodu ustawia widok aktywności na plik [activity_main.xml](https://www.google.com/search?q=activity_main.xml).

4. Upewnij się, że nazwa pliku [activity_main.xml](https://www.google.com/search?q=activity_main.xml) zgadza się z nazwą pliku, który chcesz użyć jako układ dla [MainActivity.kt](https://www.google.com/search?q=MainActivity.kt). Jeśli nazwa pliku jest inna, należy ją odpowiednio dostosować w linii kodu.

Po dodaniu linii kodu [setContentView(R.layout.activity_main)](https://www.google.com/search?q=setContentView(R.layout.activity_main)), plik [activity_main.xml](https://www.google.com/search?q=activity_main.xml) będzie używany jako układ dla [MainActivity.kt](https://www.google.com/search?q=MainActivity.kt). Będzie to oznaczać, że widok zdefiniowany w pliku [activity_main.xml](https://www.google.com/search?q=activity_main.xml) będzie wyświetlany, gdy uruchomisz aplikację i otworzysz [MainActivity](https://www.google.com/search?q=MainActivity).


----
# Virtualisation

>Enabling Virtualization (VT-x or AMD-V, SVM) in BIOS

> NOTE: If virtualization technology is enabled on your computer or you have successfully installed the emulator, ignore the explanations here.

> As I mentioned in the previous lesson, if virtualization technology is not enabled on your computer, you must enable it in order to use the emulator.

> If you’re using an Intel processor, then you have to enable **VT-x** or **VT-d** from the BIOS of your computer.

> To do so, restart your computer and open the BIOS menu. This can usually be done by pressing the **delete** key, the **F1**, **F10** key or **Alt** and **F4** keys depending on the system.

>The BIOS settings for Asus computer users are as follows.
1. Turn **ON** the System.
2. Press the **F2** key at startup BIOS Setup.
3. Press the right arrow key to the **Advanced** tab, Select **Virtualization Technology** and then press the **Enter** key.
4. Select **Enabled** and press the **Enter** key.
5. Press the **F10** key and select **Yes** and press the **Enter** key to save changes and **Reboot** into Windows.

If the manufacturer of the computer or CPU you use is different, you can find out how to do this in the BIOS with a quick google search.




-----------
# Installing the Genymotion Emulator
#android/genymotion

https://www.genymotion.com/download/

Genymotion Emulator to emulator [Androida](https://www.google.com/search?q=Androida), który jest dostępny jako usługa w chmurze oraz lokalnie dla systemów PC i Mac. Pozwala on na uruchamianie i testowanie aplikacji na wirtualnych urządzeniach z systemem [Android](https://www.google.com/search?q=Android). Oto kilka informacji na temat Genymotion Emulator:

- Genymotion jest jednym z najlepszych emulatorów [Androida](https://www.google.com/search?q=Androida) dostępnych na rynku.
- Emulator Genymotion oferuje szeroki zakres wirtualnych urządzeń, które można emulować, co umożliwia testowanie aplikacji na różnych konfiguracjach sprzętowych.
- Jest znacznie szybszy od wbudowanego emulatora [Android Studio](https://www.google.com/search?q=Android%20Studio).
- Można go używać zarówno w chmurze, jak i lokalnie na komputerze.
- Genymotion Emulator jest często wykorzystywany przez programistów do testowania i debugowania aplikacji [Androidowych](https://www.google.com/search?q=Androidowych).

Jeśli masz jakieś konkretne pytania dotyczące Genymotion Emulator, chętnie na nie odpowiem!



----------

# Gradle Build System

>[!info] Gradle
>It is a building system that automates the build of Android application development
>Gradle makes:
>	- testking
>	- building
>	- debugging
>	- releasing
>it makes easier to add new libraries to a project 

>[!info] Gradle
>  
Gradle to narzędzie do budowania projektów, które jest używane w [Android Studio](https://www.google.com/search?q=Android%20Studio). Jest to system automatycznego budowania, testowania i pakowania aplikacji [Android](https://www.google.com/search?q=Android). Gradle jest oparty na języku [Groovy](https://www.google.com/search?q=Groovy) i oferuje elastyczne i konfigurowalne możliwości kompilacji, budowania i zarządzania zależnościami w projekcie [Android](https://www.google.com/search?q=Android).


In the project `Gradle Scripts`:
- `build.gradle(Project: ...)`
- `build.gradle(Module: ...`

----
# Android Manifest file 
It is an XML page in `app/manifests/`
(to plik konfiguracyjny w systemie Android, który jest nieodłączną częścią każdej aplikacji Android   Plik [Android Manifest](https://www.google.com/search?q=Android%20Manifest) definiuje podstawowe informacje o aplikacji i jej komponentach, takich jak aktywności (activities), usługi (services), odbiorniki nadawcze (broadcast receivers) i dostawcy treści (content providers). Jest to ważny plik, który informuje system [Android](https://www.google.com/search?q=Android), jak zarządzać aplikacją i jakie funkcje są dostępne dla innych aplikacji i użytkowników.)

- it is one of the most important part for android application projects
- the basic info of our application can be accessed from this file
- we also get the basic permissions for the application in this file

`app/manifests/AndroidManifest.xml`
```xml
...
<application
			 ...
			 android:label="@string/app_name"
			 ...
```
the info about the app name is in`res/values/strings.xml` file:
```xml
<resources>
	<string name="app_name">My Android Project</string>
</resources>
```

**user permission** (e.g. to use the phone call) (add a new content):
```xml
..
<uses-permission android:name="android.permission.CALL_P"

<application
			 ...
			 android:label="@string/app_name"
			 ...
```







