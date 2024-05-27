[[_ the complete Android Kotlin]]

# Multiple Language Support

> 
> Android considers English as a default language
> 

- make a new project
- `TextView`, `Button`
- `TextView.text` > on the right side in the `Attributes` - click on `+` button
	- select `String Value`
		- resource name `hello`
		- resource value `Hello World`
		tak samo dla button i toast (`R.string.<nazwaInfoDlaTosta>`)
- otwórz `string.xml` masz na górze `open editor`
	- add `+` a new language and add analogiczne tłumaczenia dla stringów and Android add a new `string.xml` file with translation
`string.xml` (English version):
```xml
<resources>  
    <string name="app_name">MultipleLanguages</string>  
    <string name="hello">Hello World</string>  
    <string name="show_toast">show a toast message</string>  
    <string name="toast">This is a toast message </string>  
</resources>
```

a new `string.xml(pl)` with translation
```xml
<?xml version="1.0" encoding="utf-8"?>  
<resources>  
    <string name="app_name">Wiele języków</string>  
    <string name="hello">Witaj Świecie</string>  
    <string name="show_toast">pokaż wiadomość w toście</string>  
    <string name="toast">to jest nowa wiadomość</string>  
</resources>
```

- change language in your smartphone into Polish (`Settings`>`Languages`>`Add` Polish - move it as the first language)
- 


# Supporting different pixel densities
> Android Devices come different screen sizes (phone, tablets, TVs, and so on) and different pixel sizes
> 	> one device has 160 pixels per square inch, another device fits 480 pixels in the same space  
> 	> if you don't consider these variations in pixel density, the images might appear at the completely wrong size
>  

- `res`>`mipmap` > `ic_launcher` > there are icons with different density
- to make your own different icons `res` -> new -> image asset










