[[0 - wstęp do uczenia maszynowego]]

---

# Pierwszy model uczenia maszynowego

## uczenie nadzorowane - klasyfikacja

```python
import sklearn
import numpy as np
from sklearn import datasets

np.random.seed(10)
raw_data = datasets.load_iris()
print(raw_data)

```

```python
raw_data.keys()

# dict_keys(['data', 'target', 'frame', 'target_names', 'DESCR', 'feature_names', 'filename', 'data_module'])
```


### przygotowujemy dane
```python
data = raw_data.data 
target = raw_data.target

# ważnym krokiem jest sprawdzenie kształu danych
print(data.shape)
print(target.shape)

```
#### podział danych na zbiór treningowy i zbiór testowy
(czasami jeszcze zbiór walidacyjny)
```python
from sklearn.model_selection import train_test_split`

data_train, data_test, target_train, target_test = train_test_split(data, target, test_size=0.3)
```


#### tworzymy model
```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression()
model.fit(data_train, target_train)
```

#### sprawdzamy model
```python
target_pred = model.predict(data_test)

from sklearn.metrics import confusion_matrix
# pokaże błędy
confusion_matrix(target_test, target_pred)

# array([[14, 0, 0], 
#		[ 0, 17, 0],
#   	[ 0, 0, 14]])
```
chodzi o maksymalizację wartości na przekątnej (14,17,14)

#### raport
```python
from sklearn.metrics import classification_report

print(classification_report(target_test, target_pred))
```

dane testowe nie mogą być "puszczone" do modelu, bo model za bardzo się wytrenuje; trnujemy go na danych treningowych

## Ogólna procedura
1. tworzenie obiektu klasy, z której będziemy korzystać
2. trenowania modelu metodą `fit` (tu dane treningowe; zmienne niezależne(cechy) i klasy, do których te zmienne chcemy przyporządkować)
3. przewidzieć dane metodą `predict` (tu dane testowe, zmienne niezależne)
4. ocena (np. `confusion_matrix` lub `classification_report`)






