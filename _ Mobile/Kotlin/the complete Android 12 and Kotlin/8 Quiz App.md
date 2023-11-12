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
-  android:background="@drawable/bg"  
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


Add `MaterialCardView`













