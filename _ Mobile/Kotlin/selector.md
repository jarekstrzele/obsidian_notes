#andoid/selector


Plik `border_gb.xml` w folderze `drawable` z wykorzystaniem `<selector>` to plik XML definiujący zestaw stanów dla tła elementu interfejsu użytkownika. Jest to często używane do określania różnych wyglądów (np. kolory) dla różnych stanów elementu, takich jak normalny, naciśnięty (kliknięty) czy zaznaczony.

`<selector>` w pliku XML to element, który pozwala na określenie różnych obrazów lub kolorów w zależności od stanu elementu. Na przykład, może to być używane do zdefiniowania różnych kolorów tła dla przycisku w zależności od tego, czy jest w stanie normalnym, naciśniętym czy zaznaczonym.

Przykładowy plik `border_gb.xml` z `<selector>` może wyglądać mniej więcej tak:

```xml 

<selector xmlns:android="http://schemas.android.com/apk/res/android">     

<item android:state_pressed="true">         
<!-- Ustawienia dla stanu naciśniętego -->         
	<shape android:shape="rectangle">             
		<solid android:color="#FF4081" />            
		<corners android:radius="8dp" />         
	</shape>
</item>     

<item android:state_enabled="true">         
<!-- Ustawienia dla stanu normalnego -->         
	<shape android:shape="rectangle">             
		<solid android:color="#3F51B5" />             
		<corners android:radius="8dp" />  
	</shape>     
</item>     

<item android:state_enabled="false">         
<!-- Ustawienia dla stanu wyłączonego -->        
<shape android:shape="rectangle">
	<solid android:color="#9E9E9E" />            
	<corners android:radius="8dp" />         
</shape>     
</item> 
</selector>`
```


W tym przykładzie, `border_gb.xml` definiuje trzy różne stany (`pressed`, `enabled`, i `disabled`) i określa, jak mają wyglądać w tych stanach elementy UI (w tym przypadku, prostokąty z różnymi kolorami tła). Ten plik może być następnie używany jako tło dla różnych elementów, takich jak przyciski.


## inne
### `gradient`

```xml
<gradient
    android:startColor="#FF4081"
    android:endColor="#3F51B5"
    android:type="linear" />

```

### `stroke` obrys/krawędzie kształty
```xml
<stroke
    android:width="2dp"
    android:color="#000000" />


```

### `size` rozmiar kształty
```xml

<size
    android:width="100dp"
    android:height="100dp" />

```


### `padding` 
```xml
<size
    android:width="100dp"
    android:height="100dp" />

```

### `corners` promień zaokrąglenia
```xml
<corners
    android:radius="8dp" />

```

### `solid` pełen kolor wypełnienia kształtu
```xml
<solid
    android:color="#FF4081" />

```



