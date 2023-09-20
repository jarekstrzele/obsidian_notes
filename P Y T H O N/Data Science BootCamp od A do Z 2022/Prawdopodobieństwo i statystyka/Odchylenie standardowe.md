[[_wstęp statystyka]]


---

# Odchylenie standardowe ciągu
to
[[Wariancja ciągu]]

$$ 
s_n=\sqrt{
\frac{1}{n}\displaystyle{\sum_{i=1}^{n}}(x_i-\bar{x})^2
}
$$
Pierwiastek "sprawi", że dane będą przedstawione w pierwotnej skali, więc będą łatwiejsze do interpretacji

```py
var_X = 1/len(X) * ((X-X_mean)**2).sum()
var_Y = 1/len(Y) * ((Y-Y_mean)**2).sum()

std_X = np.sqrt(var_X)
std_Y = np.sqrt(var_Y)

```

w Numpy:
```py
np.std(X)
np.std(Y)
```
