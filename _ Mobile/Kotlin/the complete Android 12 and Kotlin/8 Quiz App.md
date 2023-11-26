#kotlin 

# Preparation
## no action bar
`res>values>themes>themes.xml` add:
```xml
<!-- Base application theme. -->  
<style name="Base.Theme.QuizApp" parent="Theme.Material3.DayNight.NoActionBar">  
    <!-- Customize your light theme here. -->
```


## no orientation
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


## add background
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


## Add `MaterialCardView`
>[!definition] MaterialCardView
> to część Material Design Support Library, która zapewnia elastyczny i łatwy w użyciu widok karty (card view) w aplikacjach Android. Karta jest elementem interfejsu użytkownika, który prezentuje treść w sposób logiczny i jednocześnie jest estetyczny.

>[!info] Material Design 
>to zestaw wytycznych dotyczących designu stworzonych przez Google. Jest to kompleksowy system projektowy, który obejmuje wygląd, zachowanie i interakcje w interfejsie użytkownika. Material Design został stworzony w celu zapewnienia spójnego i intuicyjnego doświadczenia użytkownika na różnych platformach i urządzeniach, począwszy od aplikacji mobilnych po strony internetowe.

### aby używać material design 
jest możliwe o ile w `build.gradle.kts`  dodano zależności ` implementation("com.google.android.material:material:1.10.0")  `
```kotlin
dependencies {  
  
    implementation("androidx.core:core-ktx:1.9.0")  
    implementation("androidx.appcompat:appcompat:1.6.1")  
    implementation("com.google.android.material:material:1.10.0")  
    implementation("androidx.constraintlayout:constraintlayout:2.1.4")  
    testImplementation("junit:junit:4.13.2")  
    androidTestImplementation("androidx.test.ext:junit:1.1.5")  
    androidTestImplementation("androidx.test.espresso:espresso-core:3.5.1")  
}

```


### użycie w pliku xml
```xml
<com.google.android.material.card.MaterialCardView  
    android:layout_width="match_parent"  
    android:layout_height="wrap_content"  
    android:layout_marginStart="20dp"  
    android:layout_marginEnd="20dp"  
    android:background="@color/white"  
    app:cardCornerRadius="28dp"  
    app:cardElevation="4dp"  
    >


</com.google.android.material.card.MaterialCardView>
```


### dodanie komponentów wewnątrz MaterialCard

#### włączenie fullscreen
in `theme.xml` add:
```xml
<!-- <item name="colorPrimary">@color/my_light_primary</item> -->  
    <item name="android:windowFullscreen">true</item>  
</
```

- `<TextView>`
- `<TextView>`
- `<TextInputLayout>` - specjalny kontener do pól tekstowych
- `<AppCompatEditText>` - rozbudowane pole tekstowe (świetnie współpracuje z MaterialDesign,  wstecza komatybilność, ...)
- `<Button>`
```xml
<LinearLayout  
    android:layout_width="match_parent"  
    android:layout_height="wrap_content"  
    android:layout_margin="16dp"  
    android:orientation="vertical">  
    <TextView        
	    android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:text="Welcome"  
        android:textSize="30sp"  
        android:textStyle="bold"  
        android:gravity="center"  
        android:textColor="#363a43"  
  
        />  
    <TextView        
	    android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:text="Please enter you name."  
        android:textSize="16sp"  
        android:textStyle="bold"  
        android:gravity="center"  
        android:textColor="#7a8089"  
        android:layout_marginTop="16dp"  
        />  
  
  
    <com.google.android.material.textfield.TextInputLayout
            android:layout_width="match_parent"  
	        android:layout_height="wrap_content"  
	        style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox"  
	        android:layout_margin="20dp"  
        >  
  
        <androidx.appcompat.widget.AppCompatEditText 
	        android:id="@+id/edit_text_name"
	        android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:hint="e.g. Jan Nowak"  
            android:inputType="textCapWords"  
            android:textColor="#363a43"  
            android:textColorHint="#7a8089"  
            />  
  
    </com.google.android.material.textfield.TextInputLayout>  
    <Button        
	    android:id="@+id/btn_start"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:layout_marginTop="16dp"  
        android:background="@color/btnColor"  
        android:backgroundTint="#293BA0"  
        android:text="START"  
        android:textColor="@color/white"  
        android:textSize="18sp" />  
  
</LinearLayout>
```


## Creating the question Model And Preparing the the question 

### a new activity
- in the package where you have `MainActivity` -> `new>Activity>ViewEmptyActivity`
- add function handler to button
```kotlin
  
class MainActivity : AppCompatActivity() {  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        setContentView(R.layout.activity_main)  
  
        val editTextName : EditText = findViewById(R.id.edit_text_name)  
        val btnStart : Button = findViewById(R.id.btn_start)  
        btnStart.setOnClickListener {  
            if(editTextName.text.isEmpty()){  
                Toast.makeText(applicationContext, "Please enter your name", Toast.LENGTH_LONG).show()  
                Log.d("mylog", "Please enter your name")  
            } else {  
                val intent = Intent(this, QuizQuestionsActivity::class.java)  
                Log.d("mylog", "ok, ${editTextName.text}")  
                startActivity(intent)  
                finish() // to finish MainActivity  
            }  
        }  
    }
```

### a new file dataclass
`>new>Kotlin>DataClass`
```kotlin
package com.example.newquizapp  
  
data class Question(  
    val id: Int,  
    val questions: String,  
    val image: Int,  
    val optionOne: String,  
    val optionTwo:String,  
    val optionThree:String,  
    val optionFour:String,  
    val correctAnswer: Int  
)
```

### a new object file
`>new>Kotlin>Object`

add `res>drawable>` files `png` with flags
```kotlin
package com.example.newquizapp  
  
object Constants {  
    fun getQuestions():ArrayList<Question>{  
        val questionsList = ArrayList<Question>()  
  
        val que1 = Question(  
            1, "What country does this flag belong to?",  
            R.drawable.ic_flag_of_argentina,  
            optionOne = "Argentina",  
            optionTwo = "Australia",  
            optionThree = "Armenia",  
            optionFour = "Austria",  
            1  
        )  
        questionsList.add(que1)
        
	return questionsList
	}
```

a new code in `QuizQuestionsActivity`:
```kotlin
class QuizQuestionsActivity : AppCompatActivity() {  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        setContentView(R.layout.activity_quiz_questions)  
  
        val questionsList = Constants.getQuestions()  
  
        Log.i("QuestionsList size is", "${questionsList.size}")  
    }  
}
```


# GUI for `quize__activity`
change main layout for `ScrollView` and add inside `LinearLayout`
```xml
<ScrollView xmlns:android="http: ... >
						
```

## first components
```xml
<?xml version="1.0" encoding="utf-8"?>  
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"  
    xmlns:app="http://schemas.android.com/apk/res-auto"  
    xmlns:tools="http://schemas.android.com/tools"  
    android:layout_width="match_parent"  
    android:layout_height="match_parent"  
    tools:context=".QuizQuestionsActivity">  
  
    <LinearLayout        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:layout_gravity="center"  
        android:gravity="center"  
        android:orientation="vertical"  
        android:padding="16dp">  
  
        <TextView            android:id="@+id/text_view_question"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:layout_gravity="center"  
            android:layout_margin="10dp"  
            android:textColor="#363a43"  
            android:textSize="22sp"  
            tools:text="What country does this flag belong to?"  
  
            />  
  
        <ImageView            android:id="@+id/image_view_image"  
            android:layout_width="wrap_content"  
            android:layout_height="wrap_content"  
            android:layout_marginTop="16dp"  
            android:contentDescription="Quiz image"  
            tools:src="@drawable/ic_flag_of_germany" />  
        <LinearLayout            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:gravity="center"  
            android:layout_marginTop="16dp"  
            android:orientation="horizontal"  
            >  
            <ProgressBar                android:id="@+id/progress_bar"  
                style="?android:attr/progressBarStyleHorizontal"  
                android:layout_width="0dp"  
                android:layout_height="wrap_content"  
                android:layout_weight="1"  
                android:max="9"  
                android:minHeight="50dp"  
                android:progress="0"  
                android:indeterminate="false"  
                />  
            <TextView  
                android:id="@+id/text_view_progress"  
                android:layout_width="wrap_content"  
                android:layout_height="wrap_content"  
                android:gravity="center"  
                android:padding="15dp"  
                android:textSize="14dp"  
                android:text="0/9" />  
  
        </LinearLayout>  
    </LinearLayout>  
</ScrollView>
```


## widgets for 4 possible answers

add four `TextView`
```xml
 <TextView  
            android:id="@+id/textview_option_four"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:layout_margin="10dp"  
            android:layout_gravity="center"  
            android:padding="15dp"  
            android:textColor="#7a8089"  
            android:textSize="10sp"  
            android:background="@drawable/default_option_border_bg"  
            tools:text="Apple"  
            />  
    </LinearLayout>  
  
</ScrollView>
```

set the coursor on `@drawable/default ...` om background and allow IDE to make a `defult_option ... `.`xml`  with 
#### [[selector]]  
```xml
<selector> .... </selector>
```

in drawable and and **change that file**:

```xml
<?xml version="1.0" encoding="utf-8"?>  
<shape xmlns:android="http://schemas.android.com/apk/res/android"  
   android:shape="rectangle"  
    >  
  
    <stroke  
        android:width="1dp"  
        android:color="#e8e8e8" />  
    <solid android:color="@color/white" />  
    <corners android:radius="15dp" />  
  
  
</shape>
```

> W skrócie, `<shape>` to predefiniowany element w Androidzie, który pozwala na definiowanie różnych kształtów graficznych i ich stylizacji za pomocą innych elementów XML, takich jak `stroke`, `solid`, `corners`, itp.
> 











