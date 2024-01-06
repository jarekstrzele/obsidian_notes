#androidmanifest

[[_ Rusz Głową Android. Programowanie aplikacji]]

>[!info] `AndroidManifest.xml`
>zawiera kluczowe informacje dotyczące aplikacji:
>- jakie aktywności,
>- jakie biblioteki,
>- ...
>Wszystkie aktywności muszą być zadeklarowane w tym pliku, aby system je widział.
```xml
<application ...
			 
	<activity  
		android:name=".CreateMessageActivity"  
		android:exported="true">  
		<intent-filter>  
		<action android:name="android.intent.action.MAIN" />  	  
		<category android:name="android.intent.category.LAUNCHER" />  
		</intent-filter>  
	</activity>

</application>
```

`<action android:name="android.intent.action.MAIN" />` główna aktywność
`<category android:name="android.intent.category.LAUNCHER" /> ` aktywność może zostać użyta do uruchomienia aplikacji

`android:name=".CreateMessageActivity" `  - obowiązkowy wiersz 
	służy do określenia klasy aktywności; `.` jest dlatego, że Android łączy nazwę klasy pakietu z nazwą klasy i w ten sposób uzyskuje pełną nazwę klasy.




