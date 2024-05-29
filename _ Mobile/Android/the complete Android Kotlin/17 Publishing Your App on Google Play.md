
# Change APK version

**Version Code**
- it is a positive integer used as an internal version number
- important number when you will update your app in Google Play
- this number is for Google Play

**Version Name**
- it is a string used as the version number shown to users
- this number is important for user

**you find these numbers in:**
`build.gradle.kt` 
```kotlin
defaultConfig {  
    applicationId = "com.js.todoapp"  
    minSdk = 24  
    targetSdk = 34  
    versionCode = 1  
    versionName = "1.0"  
  
    testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"  
}
```

When you change `versionCode` on the top you will see `Sync now` button


# Building APK File

`Build` > `Generate Signed App Bundle /APK`

`Android App Bundle` - it is a new version of Android APK (this works only in Google Play)
`APK` - a old version of Android APK (it works on Google Play and Other Platform: e.g. Amazon market)

## key store path
> [!info] key store path
> "key store path" odnosi się do ścieżki pliku `keystore`, który zawiera klucz prywatny używany do podpisywania Twojej aplikacji. 
> 
> Podpisywanie aplikacji jest kluczowym krokiem w procesie publikacji aplikacji na Google Play, ponieważ gwarantuje integralność aplikacji i pozwala użytkownikom na bezpieczne aktualizacje.


### `create new`
##### Kluczowe Informacje o Plikach `.jks`
1. **Format Pliku:**
    - `.jks` to binarny format pliku, który jest używany do przechowywania par klucz-certyfikat i certyfikatów (np. certyfikatów zaufanych stron trzecich).
2. **Użycie:**
    - **Podpisywanie Aplikacji:** Plik keystore `.jks` jest wykorzystywany do podpisywania aplikacji przed ich publikacją. Podpis cyfrowy gwarantuje, że aplikacja nie została zmodyfikowana od czasu jej podpisania przez dewelopera.
    - **Zabezpieczanie Komunikacji:** Może być również używany do przechowywania certyfikatów SSL/TLS, co jest istotne w kontekście bezpiecznej komunikacji sieciowej.


>[!danger] .jks file in Android
> - In Android if you delete this file, you will not be able to update your application.
> - You create this file once and you can use it for all your applications.

- add a password for this file in Android Studio 










