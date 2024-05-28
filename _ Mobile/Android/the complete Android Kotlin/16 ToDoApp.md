[[FileOutputStream]]
[[ObjectOutputStream]]

to add a new icon to app:
`AdroidMainfest.xml` and change: *android:icon* and *android:roundIcon*
```xml
<application  
    android:allowBackup="true"  
    android:dataExtractionRules="@xml/data_extraction_rules"  
    android:fullBackupContent="@xml/backup_rules"  
    android:icon="@drawable/todoapp_icon"  
    android:label="@string/app_name"  
    android:roundIcon="@drawable/todoapp_icon"  
    android:supportsRtl="true"
```












