#rusz_głową  #griffiths_dawn  #Griffiths_david 

---------
[[1. Skok na głęboką wodę]]
[[2. Tworzenie interaktywnych aplikacji]]
[[3 Wiele aktywności i intencji]]

-----

# Różne pojęcia

>[!definition] zasób
> dane i pliki używane przez aplikację, które same nie są kodem

>[!info] `AndroidManifest.xml`
>zawiera kluczowe informacje dotyczące aplikacji:
>- jakie aktywności,
>- jakie biblioteki,
>- ...
>Wszystkie aktywności muszą być zadeklarowane w tym pliku, aby stst
```xml
<activity  
	android:name=".CreateMessageActivity"  
	android:exported="true">  
	<intent-filter>  
	<action android:name="android.intent.action.MAIN" />  	  
	<category android:name="android.intent.category.LAUNCHER" />  
	</intent-filter>  
</activity>
```

`<action android:name="android.intent.action.MAIN" />` główna aktywność
`<category android:name="android.intent.category.LAUNCHER" /> ` aktywność może zostać użyta do uruchomienia aplikacji














