#android/listview

>[!definition] **ListView**
>
> It is a view which groups several items and display them in vertical scrollable list

# Make Toolbar:

activity_main.xml
```xml
<com.google.android.material.appbar.AppBarLayout  
    android:layout_width="match_parent"  
    android:layout_height="wrap_content"  
    android:layout_marginTop="2dp"  
    app:layout_constraintEnd_toEndOf="parent"  
    app:layout_constraintStart_toStartOf="parent"  
    app:layout_constraintTop_toTopOf="parent"  
    android:background="#123abc"  
    >  
  
    <Toolbar        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:titleTextColor="@color/white"  
        android:title="My ListView"  
        android:layout_gravity="center"  
        />  
  
</com.google.android.material.appbar.AppBarLayout>
```


# Add ListView

Palette>Legacy>ListView
or
add:
```xml
<ListView  
    android:id="@+id/listview"  
    android:layout_width="409dp"  
    android:layout_height="671dp"  
    app:layout_constraintBottom_toBottomOf="parent"  
    app:layout_constraintEnd_toEndOf="parent"  
    app:layout_constraintStart_toStartOf="parent"  
    app:layout_constraintTop_toBottomOf="@+id/appBarLayout" />
```







