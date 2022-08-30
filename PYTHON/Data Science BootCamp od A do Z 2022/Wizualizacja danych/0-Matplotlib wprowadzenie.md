[[0-Pandas wprowadzenie]]
[[2-Case Study Google App Store]]

---

# Matplotlib 
#python/matplotlib

[[#Pojedynczy wykres]]
[[#Wiele wykresów]]
[[#Wykresy słupkowe]]
[[#Wykresy punktowe]]


## Wprowadzenie
[[#Pojedynczy wykres]]
[[#Wiele wykresów]]
[[#Wykresy słupkowe]]
[[#Wykresy punktowe]]


			`pip install matplotlib`

`import matplotlib`

```py
import matplotlib
import numpy as np
import matplotlib.pyplot as plt
# aby ładnie wyglądał wykres
import seaborn as sns
sns.set()
```

Podstawowym obiektem jest obiekt typu `figure`
```py
fig = plt.figure()
fig.show()

```

---

## Pojedynczy wykres
pierwsz lista to OX, druga OY
`plt.plot([0,1], [0,3])`

![[linia_prosta_matplotlib.png]]

Ustawiamy parametry
```py
plt.plot([0,1], [0,3], label="line", color="green")
_ = plt.legend()
```

Dodajemy nowe warstwy
```py
plt.plot([0,1], [0,3], label="line", color="green")
plt.xlabel("oś x")
plt.ylabel("oś y")
plt.title("Wykres")
_ = plt.legend()
```


```py
plt.plot([0,1,2], [0,3,2], label="line", color="green")
plt.xlabel("oś x")
plt.ylabel("oś y")
plt.title("Wykres")
_ = plt.legend()
```

![[linia_prosta_matplotlib_zDodatkami.png]]

---

```py
x = np.arange(-3,3,0.1)
x_sin = np.sin(x)
x_cos = np.cos(x)

plt.plot(x, x_sin)
plt.plot(x, x_cos)

```

![[sin_cos_matplotlib.png]]

---
## Wiele wykresów
Domyślnie w komórce jest tworzony obiekt figure, ale możemy też go stworzyć samodzielnie, wówczas kontrolujemy ten obiekt.

```py
fig = plt.figure(figsize=(12,8))
# subplot(ile_wierszy, ile_kolumn, w której "komórce")
# subplot(jeden_wiersz, trzy_kolumny, ten wykres w pierwszej komórce)
plt.subplot(131)
plt.plot([0,1,2], [3,2,5])

plt.subplot(132)
plt.plot([0,1,2], [3,1,4], 'r--')

plt.subplot(133)
plt.plot([0,1,2], [3,2,5], 'ro')

```

![[trzy_wykresy_obok_matplotlib.png]]


Poza notebookie na koniec trzeba wydać komendę
`fig.show()`

---
## Wykresy słupkowe
`plt.bar(x=[0,1,2,3], height=[1.2,3.2,1.2,5.2])`
![[bar_matplotlib.png]]


`plt.barh(y=['a', 'b', 'c', 'ddd'], width=[1.2,3.2,1.2,5.2])`
![[barh_matplotlib.png]]

---

## Wykresy punktowe
```py
x1 = np.random.randn(300)
x2 = np.random.randn(300)
x3 = np.random.randn(300) * 50

# s  wielość kropek
# alpha przeźroczystość kropek 
plt.scatter(x=x1, y=x2, s=x3, alpha=0.5)
```

![[scatter_matplotlib.png]]






























