
Add new colors in `colors.xml`:
```xml
<color name="green">#028074</color>  
<color name="blue">#0479D6</color>  
<color name="ice_blue">#63B5F6</color>
```

Change `theme.xml`:
```xml
  <item name="colorPrimary">@color/green</item>  
    <item name="colorPrimaryVariant">@color/green</item>  
    <item name="colorOnPrimary">@color/white</item>  
</style>
```

Add to `activity_main.xml`:
- background
- three buttons: `ADDITION`,`SUBSTRACTION`, `MUTLIPLICATION`


![[Pasted image 20240605114748.png]]


in `MainActivity.kt`
- bindingview in gradle 
```  
buildFeatures{  
    viewBinding=true  
}
```


































