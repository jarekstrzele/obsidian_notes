[[0-Pandas wprowadzenie]]
[[Łączenie danych]]

---

# Google App Store

## Przygotowanie
```py
import pandas as pd

url = 'https://storage.googleapis.com/esmartdata-courses-files/ds-bootcamp/appstore_games.csv'
df_raw = pd.read_csv(url)
df_raw.head()

```

```py
df_raw.columns

Index(['URL', 'ID', 'Name', 'Subtitle', 'Icon URL', 'Average User Rating', 'User Rating Count', 'Price', 'In-app Purchases', 'Description', 'Developer', 'Age Rating', 'Languages', 'Size', 'Primary Genre', 'Genres', 'Original Release Date', 'Current Version Release Date'], dtype='object')


# usuwamy niepotrzebne kolumny
# standaryzujemy nazwy kolumn
df = df_raw.copy()
df=df.drop(columns=['URL', 'Icon URL', 'Subtitle', 'Description', 'In-app Purchases'])

# ustawiamy kolumnę ID jako index
df = df.set_index('ID')

# describe zostanie zastosowana do danych numerycznych
df.describe().T


# można wyświetlić statystyki innych typów
# np. object
df.decribe(include=['object']).T

# standaryzacja nazw kolumn
# wszystkie nazwy z małej litery
# spacje -> podkreślniki (możemy stosować '.')
df.columns = [col.lower().replace(' ', '_') for col in df.columns]



```

## Rozkłady poszczególnych zmiennych
Funkcja, która zwraca informację o częstości występowania danego elementu to
#python/pandas_czestosc

									`value_counts()`

```py
df.primary_genre.value_counts()

Games 16286 
Education 222 
Entertainment 198 
Utilities 77 
Sports 60 
Reference 32 
...


```


### wydobycie pięciu najbardziej popularnych
```py
df.primary_genre.value_counts().nlargest(5)

```

### stworzenie listy nazw najbardziej popularnych
```py
list(df.primary_genre.value_counts().nlargest(5).index)
```

---

### kolumna `age_rating`

```py
df.age_rating.value_counts()
4+ 11806 
9+ 2481 
12+ 2055 
17+ 665


```

```py
import seaborn as sns 
sns.set()

df.age_rating.value_counts().plot(kind='bar')
```

![[images/age_rating_bar.png]]

![[images/age_rating_pie.png]]


---

### Praca z kolumną languages
```py
# zmieniamy wartości na str i przekształcamy w listę
# chcąc pracować na tekście znowu str
# len() czyli długość każdej listy
df.languages.str.split(', ').str.len()

ID 
284921427 17.0 
284926400 1.0 
284946595 1.0 
285755462 17.0
...

# dodajemy nową kolumnę z informacją, ile języków ma dana appka
df['num_lang'] = df.languages.str.split(', ').str.len()

# teraz łatwo dowiemy się, ile jest aplikacji z daną ilością języków
df.num_lang.value_counts()



```

---

## Braki danych
Gdy chcemy uwzględnić dane NaN
`df.average_user_rating.value_counts(dropna=False)`

#python/maska_logiczna 
#python/nan 
`df.isnull()` ->  False, czyli nie ma nulla
						True, czyli null jest

```py
df.isnull.summ() # -> null +1, nie_null +0
name 0 # nie ma nulla
average_user_rating 9446 
user_rating_count 9446 
price 24 # tu są 24 nulle
developer 0 
age_rating 0 
languages 60 
size 1 
...
```

funkcja `dropna()` usuwa null
```py
df = df.dropna()
df.isnull().sum()
name 0 
average_user_rating 0 
user_rating_count 0 
price 0 
...


```




















