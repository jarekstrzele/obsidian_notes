


[[_wstęp statystyka]]



# Średni błąd

średni błąd ciągu wartości $x_1,...,x_n$ nazywamy wartość 
$$ 
b=\frac{1}{n}\displaystyle{\sum_{i=1}^{n}}|x_i-\bar{x}|
$$

to średnia odległość od średniej

==Im mniejszt jest średni błąd tym zmienna $X$ ma mniejszy rozrzut==

przykład
$\bar{X}=\frac{3.5+4.0+4.0}{3}=3.83$
$\bar{Y}=\frac{2.0+4.0+5.0}{3}=3.67$

zatem
$b_X=\frac{1}{3}(|3.5-3.83|+|4.0-3.83|+|4.0-3.83|=0.2222$

```py
X=[3.5,4.0,4.0]
Y=[2.0,4.0,5.0]

X_mean=np.mean(X)
Y_mean=np.mean(Y)

b_X = 1/len(X) * (abs(X-X_mean).sum())
b_y = 1/len(Y) * (abs(Y-Y_mean).sum()) 

```
$b_X =0.2222$
$b_Y=1.1111$



