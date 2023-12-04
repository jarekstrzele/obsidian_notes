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

Wewnątrz MaterialCardView dodaj: 
- `<TextView>`
- `<TextView>`
- `<TextInputLayout>` - specjalny kontener do pól tekstowych
- `<AppCompatEditText>` - rozbudowane pole tekstowe (świetnie współpracuje z MaterialDesign,  wstecza komatybilność, ...)
- `<Button>`
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
            android:background="#C4D6D9"  
            android:backgroundTint="#293BA0"  
            android:text="START"  
            android:textColor="@color/white"  
            android:textSize="18sp"  
            style="@style/Theme.NewQuizApp"  
            />  
  
    </LinearLayout>  
  
  
</com.google.android.material.card.MaterialCardView>
```


## Creating the question Model And Preparing the the question 

### a new activity
- in the package where you have `MainActivity` -> `new>Activity>ViewEmptyActivity`
- add function handler to button in `MainActivity`
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

>[!important] Identyfikator zasobów (`image: Int`)
> W Androidzie identyfikatory zasobów są liczbami całkowitymi (integer), reprezentującymi unikalne identyfikatory zasobów.
> 
> Chociaż w `image:Int` będziemy:
> 	-  przekazywać ścieżkę dostępu do obrazka (np. `R.drawable.ic_flag_of_belgium`, który wydaje się być ciągiem znaków), 
> 	- w rzeczywistości jest to liczba całkowita, która jest identyfikatorem zasobu. 
> 
> W związku z tym przypisanie go do pola `image` w klasie `Question` jest zgodne z oczekiwaniami, ponieważ oczekuje ono wartości typu `Int`.

----
### add `res>drawable>` files `png` with flags


----
### a new object file
`>new>Kotlin>Object` -> create a `Constant` file name
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
make other questions in the same way


a new code in `QuizQuestionsActivity` (in the some folder that `MainActivity.kt`):
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
change main layout for `ScrollView` and add inside it  `LinearLayout`
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
you are in `<TextView>`  > add `android::background`
>`android:background="@drawable/default_option_border_bg` (the name *default_op...* is arbitrary)
set the coursor on `@drawable/default ...` on background and allow IDE to make a `defult_option ... `.`xml`  with *create resource .... *

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

and at the end add `Button`:
```xml
 <Button  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:layout_margin="10dp"  
            android:background="@color/design_default_color_primary"  
            android:text="SUBMIT"  
            android:textColor="@android:color/white"  
            android:textSize="10sp"  
            android:textStyle="bold" />  
        </LinearLayout>  
  
</ScrollView>
```

-------
## Adding the button functionality to the questions activity

### add `selected_option_border_bg.xml`
in `drawable` folder > new > Drawable resource file > *selected_option_border_bg*

copy content from `default_option_border_bg.xml` and paste it into the new file `selected_option_border_bg.xml`
and change `color` in `stroke` into <stroke  
    android:width="5dp"  
    android:color="@color/design_default_color_primary" />`<stroke android:width="5dp"     android:color="@color/design_default_color_primary" />`
    
### add button submit handler 

- in `active_quiz_questions` add id to the button
```xml
<Button  
    android:id="@+id/btn_submit"
```

in `QuizQuestionActivity.kt`:
```kotlin
...
private var btnSubmit: Button? = null  
  
override fun onCreate(savedInstanceState: Bundle?) {

...

	btnSubmit = findViewById(R.id.btn_submit)
```



### add `View.OnClickListener` to `QuizQuetionsActivity`
>Implementując interfejs `View.OnClickListener`, klasa QuizQuestionsActivity zyskuje zdolność do nasłuchiwania zdarzeń kliknięć na widokach. Po zaimplementowaniu tego interfejsu, klasa musi dostarczyć implementację metody `onClick`, co umożliwia reakcję na kliknięcia użytkownika.

`View.OnClickListener` it is a interface.
```kotlin
class QuizQuestionsActivity : AppCompatActivity(), View.OnClickListener {
...
override fun onCreate(){....}

override fun onClick(p0: View?){
 TODO("Not yet implemented")
}
```


#### Add some code to the `QuizQuestionsActivity`
```kotlin
  
class QuizQuestionsActivity : AppCompatActivity(), View.OnClickListener {  
  
private var mCurrentPosition: Int = 1  
private var mQuestionsList: ArrayList<Question>?= null  
private var mSelectedOptionPosition: Int = 0  
  
private var progressBar: ProgressBar? = null  
private var textViewProgress: TextView? = null  
private var textViewQuestion: TextView? = null  
private var imageView: ImageView? = null  
  
private var textViewOptionOne: TextView? =null  
private var textViewOptionTwo: TextView? =null  
private var textViewOptionThree: TextView? =null  
private var textViewOptionFour: TextView? =null  
  
private var btnSubmit: Button? = null  
  
override fun onCreate(savedInstanceState: Bundle?) {  
super.onCreate(savedInstanceState)  
setContentView(R.layout.activity_quiz_questions)  
  
progressBar = findViewById(R.id.progress_bar)  
textViewProgress = findViewById(R.id.text_view_progress)  
textViewQuestion = findViewById(R.id.text_view_question)  
imageView = findViewById(R.id.image_view_image)  
textViewOptionOne = findViewById(R.id.textview_option_one)  
textViewOptionTwo = findViewById(R.id.textview_option_two)  
textViewOptionThree = findViewById(R.id.textview_option_three)  
textViewOptionFour = findViewById(R.id.textview_option_four)  
btnSubmit = findViewById(R.id.btn_submit)  
  
mQuestionsList = Constants.getQuestions()  
  
setQuestion()  
}  
  
private fun setQuestion() {  
  
  
val question: Question = mQuestionsList!![mCurrentPosition - 1]  
  
imageView?.setImageResource(question.image)  
progressBar?.progress = mCurrentPosition  
textViewProgress?.text = "$mCurrentPosition/${progressBar?.max}"  
  
textViewQuestion?.text = question.question  
textViewOptionOne?.text = question.optionOne  
textViewOptionTwo?.text = question.optionTwo  
textViewOptionThree?.text = question.optionThree  
textViewOptionFour?.text = question.optionFour  

if(mCurrent)
}  
  
override fun onClick(p0: View?) {  
TODO("Not yet implemented")  
}  
}
```

### add a new function `defaultOptionsView`
### In the file `QuizQuestionsActivity`
when a option will be clicked other become gray

#### `defaultOptionsView()`
you can test it calling this function after `setQuestion()`
```kotlin
private fun defaultOptionsView(){  
val options = ArrayList<TextView?>();  
textViewOptionOne.let{  
options.add(0, it)  
}  
textViewOptionTwo.let{  
options.add(1, it)  
}  
textViewOptionThree.let{  
options.add(2, it)  
}  
textViewOptionFour.let{  
options.add(3, it)  
}  
  
for(option in options){  
option?.setTextColor(Color.parseColor("#7a8089"))  
//option?.setTextColor(Color.parseColor("#ff0000")) // for testing purpose  
option?.typeface = Typeface.DEFAULT // jaka będzie domyślna czcionka, inne wartości  
// Typeface.DEFAULT_BOLD (domyślna czcionka pogrubiona) lub Typeface.ITALIC (kursywa).  
option?.background = ContextCompat.getDrawable(  
this,  
R.drawable.default_option_border_bg  
// R.drawable.selected_option_border_bg  
)  
  
}  
}
```


#### `selectedOptionView()`
 ```kotlin
 override fun onClick(view: View?) {  
when(view?.id){  
R.id.textview_option_one -> {  
textViewOptionOne?.let{  
selectedOptionView(it, 1)  
}  
}  
  
R.id.textview_option_two -> {  
textViewOptionTwo?.let{  
selectedOptionView(it, 2)  
}  
}  
  
R.id.textview_option_three -> {  
textViewOptionThree?.let{  
selectedOptionView(it, 3)  
}  
}  
  
R.id.textview_option_four -> {  
textViewOptionFour?.let{  
selectedOptionView(it, 4)  
}  
R.id.btn_submit -> {  
// TODO "implement submit buttom"  
}
}  
}  
}
```

add onClick to these TextViews
inside `onCreate` method 
```kotlin
mQuestionsList = Constants.getQuestions()  
  
textViewOptionOne?.setOnClickListener(this)  
textViewOptionTwo?.setOnClickListener(this)  
textViewOptionThree?.setOnClickListener(this)  
textViewOptionFour?.setOnClickListener(this)  
btnSubmit?.setOnClickListener(this)  
  
setQuestion()  
//defaultOptionsView() //for testing purpose
```






















