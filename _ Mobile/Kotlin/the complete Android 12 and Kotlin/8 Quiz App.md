#kotlin 

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


### Add `MaterialCardView`
>[!definition] MaterialCardView
> to część Material Design Support Library, która zapewnia elastyczny i łatwy w użyciu widok karty (card view) w aplikacjach Android. Karta jest elementem interfejsu użytkownika, który prezentuje treść w sposób logiczny i jednocześnie jest estetyczny.

>[!info] Material Design 
>to zestaw wytycznych dotyczących designu stworzonych przez Google. Jest to kompleksowy system projektowy, który obejmuje wygląd, zachowanie i interakcje w interfejsie użytkownika. Material Design został stworzony w celu zapewnienia spójnego i intuicyjnego doświadczenia użytkownika na różnych platformach i urządzeniach, począwszy od aplikacji mobilnych po strony internetowe.













