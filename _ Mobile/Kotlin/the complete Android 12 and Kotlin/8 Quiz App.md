#kotlin 

# Preparation
## no action bar
`res>values>themes>themes.xml` add:
```xml
<!-- Base application theme. -->  
<style name="Base.Theme.QuizApp" parent="Theme.Material3.DayNight.NoActionBar">  
    <!-- Customize your light theme here. -->
```


## no orientation
`AndroidManifest.xml`
no rotation, only portrait
add `screenOrientation`
```xml
<activity  
    android:name=".MainActivity"  
    android:exported="true"
    android:screenOrientation="portrait"
		  >
```


## add background
- `res>drawable` add `.png` background
- use LinearLayout

`activity_main.xml`
add:
-  android:background="@drawable/bg"   (drop the image file.png into `drawable`); `bg` it is a name of the image file
-  android:text="Quiz App"  
- android:textSize="25sp"  
- android:textStyle="bold"
```xml
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"  
    xmlns:app="http://schemas.android.com/apk/res-auto"  
    xmlns:tools="http://schemas.android.com/tools"  
    android:layout_width="match_parent"  
    android:layout_height="match_parent"  
    android:background="@drawable/bg"  
    tools:context=".MainActivity">  
  
    <TextView
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:text="Quiz App"  
        android:textSize="25sp"  
        android:textStyle="bold"  
        android:gravity="center"  
        android:textColor="@color/white"  
  
        />  
  
</LinearLayout>
```


## Add `MaterialCardView`
>[!definition] MaterialCardView
> to część Material Design Support Library, która zapewnia elastyczny i łatwy w użyciu widok karty (card view) w aplikacjach Android. Karta jest elementem interfejsu użytkownika, który prezentuje treść w sposób logiczny i jednocześnie jest estetyczny.

>[!info] Material Design 
>to zestaw wytycznych dotyczących designu stworzonych przez Google. Jest to kompleksowy system projektowy, który obejmuje wygląd, zachowanie i interakcje w interfejsie użytkownika. Material Design został stworzony w celu zapewnienia spójnego i intuicyjnego doświadczenia użytkownika na różnych platformach i urządzeniach, począwszy od aplikacji mobilnych po strony internetowe.

### aby używać material design 
jest możliwe o ile w `build.gradle.kts`  dodano zależności ` implementation("com.google.android.material:material:1.10.0")  `
```kotlin
dependencies {  
  
    implementation("androidx.core:core-ktx:1.9.0")  
    implementation("androidx.appcompat:appcompat:1.6.1")  
    implementation("com.google.android.material:material:1.10.0")  
    implementation("androidx.constraintlayout:constraintlayout:2.1.4")  
    testImplementation("junit:junit:4.13.2")  
    androidTestImplementation("androidx.test.ext:junit:1.1.5")  
    androidTestImplementation("androidx.test.espresso:espresso-core:3.5.1")  
}

```


### użycie w pliku xml
```xml
<com.google.android.material.card.MaterialCardView  
    android:layout_width="match_parent"  
    android:layout_height="wrap_content"  
    android:layout_marginStart="20dp"  
    android:layout_marginEnd="20dp"  
    android:background="@color/white"  
    app:cardCornerRadius="28dp"  
    app:cardElevation="4dp"  
    >


</com.google.android.material.card.MaterialCardView>
```


### dodanie komponentów wewnątrz MaterialCard

in `theme.xml` add:
```xml
<!-- <item name="colorPrimary">@color/my_light_primary</item> -->  
    <item name="android:windowFullscreen">true</item>  
</
```

- `<TextView>`
- `<TextView>`
- `<TextInputLayout>` - specjalny kontener do pól tekstowych
- `<AppCompatEditText>` - rozbudowane pole tekstowe (świetnie współpracuje z MaterialDesign,  wstecza komatybilność, ...)
- `<Button>`
```xml
<LinearLayout  
    android:layout_width="match_parent"  
    android:layout_height="wrap_content"  
    android:layout_margin="16dp"  
    android:orientation="vertical">  
    <TextView        
	    android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:text="Welcome"  
        android:textSize="30sp"  
        android:textStyle="bold"  
        android:gravity="center"  
        android:textColor="#363a43"  
  
        />  
    <TextView        
	    android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:text="Please enter you name."  
        android:textSize="16sp"  
        android:textStyle="bold"  
        android:gravity="center"  
        android:textColor="#7a8089"  
        android:layout_marginTop="16dp"  
        />  
  
  
    <com.google.android.material.textfield.TextInputLayout        android:layout_width="match_parent"  
        android:layout_height="wrap_content">  
  
    </com.google.android.material.textfield.TextInputLayout>
    
    
</LinearLayout>
```


## Creating the question Model And Preparing the the question




















