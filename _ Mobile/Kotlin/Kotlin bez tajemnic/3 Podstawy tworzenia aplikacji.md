[[_ Kotlin bez tajemnic]]

# Android Studio 
- `File>Settings>Plugin`:
	- rainbow brackets
	- nyan progress bar


# Activity and lifecycle

- `: AppCompatActivity()` dziedziczenie po tej klasie sprawia, że dana klasa jest `activity`
- definicja startowej aktywności  oraz wszystkie pozostałe aktywnośći w `AndroidManifest`

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









