# 200 ćw. Python

#python/f-string

`pi=3.1415926535

`print(f'Przybliżenie liczby pi: {pi:.2f}')` 

`print('summer', 'time', 'holiday', sep='#')`

```python
pv = 1000
r = 0.03
n = 5
fv = pv * (1 + r) ** n
print(f'Wartość końcowa inwestycji wynosi: {fv:.2f} PLN')
```
pv - pieniądze
r - odsetki
n - czas oszczędzania
`fv=pv * (1+r) **n` ile będzie po n latach oprocentowanych r


---
## wycinanie
#python/wycinanie
```python

filename = 'view.jpg'
roz = filename[-3:]
print(f'{roz}')
```

binarnie
```python
string = '1 0 0 1 0 1'
binary = string[::2]
number = int(binary, 2)
print(f'Znaleziona liczba: {number}')

```

odwrócony tekst
```python
text = 'Kurs Python'
print(text[::-1])
```

----
## string
#python/string

zmiana pierwszej litert na dużą
```python
text = 'python jest popularnym językiem programowania.'
print(text.capitalize())
```

ile razy 'p'
```python
text = 'python jest popularnym językiem programowania.'
print(f"Liczba wystąpień: {text.count('p')}")
```

czy string jest alfanumeryczny (cyfry+litert)
```python
code1 = 'FVNISJND-20'
code2 = 'FVNISJND20'

print(f"code1: {code1.isalnum()}")
print(f"code2: {code2.isalnum()}")
```

bez spacji na początku u końcu
```python
text = '  Google Colab   '

print(text.strip())

```

zamień `'-'` na `' '`
```python
code = 'FVNISJND-XX'
print(code.replace('-',' '))

text = '340-23-245-235'
print(text.replace('-', ''))
```

z string do listy
```python
text = 'Open,High,Low,Close'
print(text.split(','))
```

`splitlines()` Splits the string at line breaks and returns a list
podziel string aby otrzymać listę bez znaku `\n` nowej linii
```python
text = """Python jest językiem ogólnego przeznaczenia.
Python jest popularny."""
print(text.splitlines())
```

`zfill()` Fills the string with a specified number of 0 values at the beginning
```python
num = 34
print(str(num).zfill(6))
```
----
## Struktury danych


### zbiory
`nazwa_zbioru.add(new_elem)`
```python
vowels = {'a', 'e', 'i', 'o', 'u'}

text = 'Programming in python.'
text = text.lower()
text = text.replace(' ', '')
text = text.replace('.', '')
letters = set(text)
consonants = letters.difference(vowels)
print(f'Liczba elementów: {len(consonants)}')
```

**difference(arg)** - Returns a set containing the difference between two or more sets

 różnica symetryczna
 ```python
 A = {2, 4, 6, 8}
B = {4, 10}

print(f'Różnica symetryczna: {A.symmetric_difference(B)}')
```
output: Różnica symetryczna: {2, 6, 8, 10}

----
### tuples

```python 
wig20 = ('CDR', 'PKO', 'PEO')
mwig40 = ('PLW', 'AMC', 'BFT')
result = wig20 + mwig40
print(result)
```
```python
a = (*wig20, *mwig40)
print(a)
```

```python
default = ('YES', 'NO', 'NO', 'YES', 'NO')
print(f'Liczba wystąpień: {default.count("YES")}'}
```

```python
default = ('YES', 'NO', 'NO', 'YES', 'NO')
print(f"Liczba wystąpień: {default.count('YES')}")
```

```python
names = ('Monika', 'Tomek', 'Adam', 'Olaf')
sorted_names = tuple(sorted(names))
print(sorted_names)
```
`sorted()` zwraca listę

SORTOWANIE Z `key` po drugim elemencie wewnętrznych krotek
```python
info = (('Monika', 19), ('Tomek', 21), ('Adam', 18), ('Jarek', 30))
asc = tuple(sorted(info, key=lambda item: item[1]))
desc = tuple(sorted(info, key=lambda item: item[1], reverse=True))
print(f'Rosnąco: {asc}')
print(f'Malejąco: {desc}')
```



----
## Listy
#python/list
```python
idx = ['001', '002', '001', '003', '001']
num = idx.count('001')
print(f'Liczba wystąpień: {num}')
```

```python
text = 'Programowanie w języku Python'
text_trans = text.lower()
text_trans = text_trans.replace("ę", "e")
text_trans = list(set(text_trans))
text_trans.remove(' ')
text_trans = sorted(text_trans)
print(text_trans[:10])
```

```python
filenames = ['view.jpg', 'bear.jpg', 'ball.png']
filenames.insert(0,'phone.jpg')
filenames.remove('ball.png')
print(filenames)
```

```python
techs = ('python', 'java', 'sql', 'aws')
techs = tuple(sorted(techs))
print(techs)
```

```python
hashtags = ['summer', 'time', 'vibes']
print('#' + '#'.join(hashtags))
```

---
## słowniki
#python/dictionary

`dict.keys()`
`dict.values()`
`dict.items()`


```python
stocks = {
    'PLW': {'Playway': 316},
    'CDR': {'CD Projekt': 293},
    'TEN': {'Ten Square Games': 301}
}
print(stocks['PLW'])
```
output: {'Playway': 316} 

z listy na listę (index, value)
```python
ticker = [
    'ALR', 'CCC', 'CDR', 'CPS', 'DNP',
    'JSW', 'KGH', 'LPP', 'LTS', 'MBK',
    'OPL', 'PEO', 'PGE', 'PGN', 'PKN',
    'PKO', 'PLY', 'PZU', 'SPL', 'TPE'
]
tmp = list(enumerate(ticker))
```

z listy na słownik
`dict(enumarate(ticker))`

`sorted(list(set(project_ids.values()))) print(tmp)`

to delete
```python
stats = {'strona': 'e-smartdata.org', 'ruch': 100, 'typ': 'organiczny'}
del stats['ruch']
print(stats)

# or
# tats.pop('ruch')
```


```python
users = {'001': 'Marek', '002': 'Monika', '003': 'Jakub'}
print(users.get('004', 'nieokreślony'))
```

---
# Obsługa wyjątków
```python
suma = 3000
counter = 0

try:
    result = suma / counter
    print(result)
except ZeroDivisionError:
    print('Dzielenie przez zero.')
```

```python
try:
    with open('file.txt', 'r') as file:
         content = file.read()
except FileNotFoundError:
    print('Nie znaleziono pliku.')
```


---
# input out put

```python
with open('plw_d.csv', 'r') as file:
    content = file.read().splitlines()


data = [(line.split(',')[0], line.split(',')[4]) for line in content]
print('data',data)
result = { 
    data[0][0]: [data[1:][i][0] for i in range(len(data) - 1)],
    data[0][1]: [float(data[1:][i][1]) for i in range(len(data) - 1)],
}
print(result)

#result = { }
#data = [d.split(',')[0] for d in content[1:]]
#zamk = [float(z.split(',')[-2]) for z in content[1:]] 
#result = {"Data": data, "Zamknięcie": zamk}
#print(result) i

################
data = [int(vol.split(',')[-1]) for vol in content[1:] ]
print(f"Max Vol: {max(data)}")

#################
row_data = [ i.split(',') for i in content[1:] ]
data = [int(vol[-1]) for vol in row_data ]
max_vol = str(max(data))
max_data = ""
# zamiast for można
# max_data = list(filter(lambda x: max_vol == x[-1] , row_data))[0][0]
for i in row_data:
    if i[-1] == max_vol:
        max_data = i[0]

print(f"Data: {max_data}")



```

----
### zapisanie do pliku
#python/write
```python
with open("num.txt", "a") as f:
    for i in range(2, 20, 2):
        f.write(str(i) +"\n")
```

----
## JSON
[[Python JSON]]
[[Pretty Print]]


```python
import json
  
stocks = {'PLW': ['Playway', 350], 'BBT': ['Boombit', 22]}
 
with open('stocks.json', 'w') as file:
    json.dump(stocks, file, indent=4)
```


```python
headers = ['user_id', 'amount']
users = [['001', '1400'], ['004', '1300'], ['007', '900']]
 
with open('users.csv', 'w') as file:
    file.write(','.join(headers) + '\n')
    for user in users:
        file.write(','.join(user) + '\n')
```


-----
## Funkcje
### built-in
`eval()` evaluates the sepcified expression, if the expression is a legal Pytho statemn
`eval(expression, globals, locals)`
https://www.w3schools.com/python/ref_func_eval.asp

```python
x = -1.5
expression = 'x**2 + x'
print(eval(expression)) # -> 0.75
```



`isinstance(what, type)`

#python/zip
`zip()` returns a sip object which is an iterator of tuples where the first item in each passed iterator i paired together
`zip(iterator1, iterator2, ...)`
```python
ticker = ('TEN', 'PLW', 'CDR')
full_name = ('Ten Square Games', 'Playway', 'CD Projekt')
print(list(zip(ticker, full_name)))
```


#python/all
```python
items = (' ', '0', 0.1, True)
print(all(items)) # -> True, czyli wszystkie elementy krotki są 

items = ('', 0.0, 0, False)
print(any(items)) # -> False, czy jakikolwiek element krotki jest prawdziwy
```


zliczanie ilości jedynek w reprezentacji binarnej
```python
number = 234
binary = bin(number)
binary = binary[2:]
print(binary.count('1'))
```

Czy lista zawiera unikalne wartości?
```python
def is_distinct2(items):
  return len(items) == len(set(items))

```

#python/sorted
sortowanie po drugim elemencie krotki
```python
def sort_list(lista):
    return sorted(lista, key=lambda item: item[1])
```

#python/sort
sortowanie po kluczu 'price'
```python
stocks = [
    {'indeks': 'mWIG40', 'name': 'TEN', 'price': 304},
    {'indeks': 'mWIG40', 'name': 'PLW', 'price': 309},
    {'indeks': 'sWIG80', 'name': 'BBT', 'price': 22}
]
stocks.sort(key=lambda item: item["price"])
print(stocks)
```

sortowanie po sumie kwadratów krotki
```python
items = [(3, 4), (2, 5), (1, 4), (6, 1)]
items.sort(key=lambda item: item[0]**2+item[1]**2)
print(items)
```


#python/filter 
lista tylko z jednym rodzajem indeksu
```python
stocks = [
    {'indeks': 'mWIG40', 'name': 'TEN', 'price': 304},
    {'indeks': 'mWIG40', 'name': 'PLW', 'price': 309},
    {'indeks': 'sWIG80', 'name': 'BBT', 'price': 22}
]
nWIG49 = list(filter(lambda item: item['indeks']=='mWIG40', stocks))
print(nWIG49)
```

wytnij z elementów listy `-`
```python
items = ['P-1', 'R-2', 'D-4', 'F-6']
print(list(map(lambda s: s.replace('-',''), items)))
```

#python/map 
dwie listy przekształcić w jedną (reszta z dzielenia pierwszej prze drugą)
```python
num1 = [4, 2, 6, 2, 11]
num2 = [5, 2, 3, 3, 9]

print(list( map( lambda x, y: x % y, num1,
```

-----
## generatory
#python/generator 
[[3 Generatory]]

```python
fnames = ['data1.txt', 'data2.txt', 'data3.txt', 'view.jpg']

def file_gen(lista):
  for i in lista:
    if i.endswith('.txt'):
      yield i 

f = file_gen(fnames)
```

----
## set comprehension
metoda tworzenia zbiorów z iteratorów
`newSet={expression for element in  iterable}`

prawdopodobieństwo wyrzucenia (dwa rzuty) więcej niż 10 oczek:
```python
omega = {(i, j) for i in range(1, 7) for j in range(1, 7)}
sum_gt_10 = {pair for pair in omega if pair[0] + pair[1] > 10}
print(f'P-stwo: {len(sum_gt_10) / len(omega):.2f}')

```

```python
omega = {(x,y) for x in range(1,7) for y in range(1,7)}
# Prawdopodobieństwo suma kwadratów oczek wyższa lub równa 45
a = { (x,y) for x,y in omega if (x**2 + y**2) >= 45}
pr_stwo = round(len(a)/len(omega), 2)
print(f'P-stwo:{pr_stwo}')
```

----
## dict comprehension
#python/dict_comprehension

`print({a:a**2 for a in range(1,8)})`


----
# pakiety wbudowane
#python/built-in
### calendar
kalendarz na rok 2020
```python
import calendar
print(calendar.calendar(2020))
```
#python/calendar


tylko jeden miesiąc
```
print(calendar.month(2020, 6))
```

### datetime
#python/datetime 
```python
import datetime
data1 = datetime.datetime(2020,6,1)
data2 = datetime.datetime(2020, 7, 18)
print(data2-data1)
```


### re
#python/re 
znajdź wszystkie wystapienia cyfr
```python
import re
string = "Python 3.8"
print(re.findall(pattern=r'\d', string))
# output: ['3', '8']

```

znajdź wszystkie znaki alfanumeryczne
```python
import re


string = '!@#$%^&45wc'
print(re.findall(pattern=r'\w', string=string))

```


znajdź wszystkie adresy email
```python
import re


raw_text = "Wyślij email na adres: info@template.com lub sales-info@template.it"
print(re.findall(pattern=r'[\w\.-]+@[\w\.-]+', string=raw_text))
```

`.` any character
`\.` dot
`[]` set of character
`\w` matches any: a-Z, 0-9 _ 
`\s` returns a match where the string contains a white space character

DZIELENIE tekstu względem spacji przy użyciu modułu `re`
```python
import re
 
 
text = 'Programowanie w języku Python - od A do Z'
result = re.split(pattern=r"\s+", string=text)
print(result
```

### string
#python/string 

#### constants
```python
import string

# string module constants
print(string.ascii_letters)
print(string.ascii_lowercase)
print(string.ascii_uppercase)
print(string.digits)
print(string.hexdigits)
print(string.whitespace)  # ' \t\n\r\x0b\x0c'
print(string.punctuation)
```
output
abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
abcdefghijklmnopqrstuvwxyz
ABCDEFGHIJKLMNOPQRSTUVWXYZ
0123456789
0123456789abcdefABCDEF
 	

!"#$%&'()*+,-./:;?@[\]^_`{|}~


### collections
this module implements specialized container datatypes providing alternatives to Python's general purpose built-in containers (`dict, list, set, tuple`):
- `namedtuple()` factory function for creating tuple cubclasses with named fields
- `Counter` dict subclass for counting hasavle objects
```python
>>> # Tally occurrences of words in a list
>>> cnt = Counter()
>>> for word in ['red', 'blue', 'red', 'green', 'blue', 'blue']:
...     cnt[word] += 1
>>> cnt
Counter({'blue': 3, 'red': 2, 'green': 1})

>>> # Find the ten most common words in Hamlet
>>> import re
>>> words = re.findall(r'\w+', open('hamlet.txt').read().lower())
>>> Counter(words).most_common(10)
[('the', 1143), ('and', 966), ('to', 762), ('of', 669), ('i', 631),
 ('you', 554),  ('a', 546), ('my', 514), ('hamlet', 471), ('in', 451)]
```
- ...

zlicz częstość występowania elementu
```python
# pierwszy sposób
from collections import Counter
 
 
counter = Counter()
items = ['YES', 'NO', 'NO', 'YES', 'EMPTY', 'YES', 'NO']
for item in items:
    counter[item] += 1
print(counter)

# drugi sposób
counter = Counter(items)
print(counter)


```


### random
pseudolosowe wybranie elementu z sekwencji
```python
import random


random.seed(12)

items = ['python', 'java', 'sql', 'c++', 'c']
print(random.choice(items))
```

`seed()` initialize the random number generator
`choice()` returns a random element from the given sequence
`choices()` return a list with random selsction from the given sequence

losowe przemieszanie elementów sekwencji
```python
import random


random.seed(15)

items = ['python', 'java', 'sql', 'c++', 'c']
# tutaj wpisz swoje rozwiązanie
random.shuffle(items)
print(items)
```


### pickle
#python/pickle #python/marshalling
https://realpython.com/python-pickle-module/

>[!serialization]
>**serialization** a way to conver a data structure into a linear form that can be stored or transmitted over a network
>> in python: a complex object structure ->  stream of butes **marshalling

>[!deserialization]
>  **deserialization** **unmarshelling** the reverse process, which takes a stream of bytes and converts it back into a data structure

in python there are three modules that allows you to serialize and deserialize object:
- `marshal`
- `json`
- `pickle`
- 

zapisanie listy ids do pliku data.pickle
```python
import pickle
 
 
ids = ['001', '003', '011']
 
with open('data.pickle', 'wb') as file:
    pickle.dump(ids, file)
```

```python
import json
 
 
stocks = {'PLW': 360.0, 'TEN': 320.0, 'CDR': 329.0}
result = json.dumps(stocks, sort_keys=True, indent=4)
print(result)
```

---
#python/mae
```python
# Mean Absolute Error dokładność modelu uczenia maszynowego (modele regresyjne)
# mae 1/n * suma_od_i=1_do_n|y_pred_i - y_true_i
y_true = [10,10.5, 11.2, 10.4]
y_pred=[10.2, 10.4, 10.8, 11.0]

def mae(y_true, y_pred):
  errors = [abs(yp - yt) for yt, yp in zip(y_true, y_pred)]
  n = len(y_true)
  return round(sum(errors)/n, 3)

print(mae(y_true, y_pred))
```

#python/mse
```python
# Mean Squared Error dokładność modelu uczenia maszynowego (modele regresyjne)
y_true = [10,10.5, 11.2, 10.4]
y_pred=[10.2, 10.4, 10.8, 11.0]

def mse(y_true, y_pred):
  errors = [(yp - yt)**2 for yt, yp in zip(y_true, y_pred)]
  n = len(y_true)
  return round(sum(errors)/n, 3)

print(mse(y_true, y_pred))
```

#python/identity_matrix
```python
def identity(number):
  tmp = [ [0]*number for _ in range(number)]
  for idx, item in enumerate(tmp):
    item[idx]=1
  return tmp

identity(3)
```

#python/trace
```python 
# ślad macierzy suma po przekątnej
def trace(matrix):
  return sum([ item[idx] for idx, item in enumerate(matrix) ])
```
