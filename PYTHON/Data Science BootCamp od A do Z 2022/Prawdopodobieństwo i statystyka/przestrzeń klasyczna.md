[[przestrzeń probabilistyczna]]


---

### Przestrzeń klasyczna
$\Omega$ jest zbiorem skończonym składającym się z $n$ jednakowo prawdopodobnych zdarzeń elementarnych:
$$
\Omega=\{\omega_1,..., \omega_n \}
$$

Jeśli $A \in F$, to: 
$$
P(A) = \frac{\# A}{n}
$$

przykład:
$\Omega=\{1,2,3,4,5,6 \}$
$A$ zdarzenie polegające na wyrzuceniu liczby parzystej
$n = 6$
$A=\{2,4,6\}$
$\#A=3$
stąg $P(A)=\frac{\#A}{n}=\frac{3}{6}=\frac{1}{2}$

```py
omega = {1,2,3,4,5,6}
A = {item for item in omega if item % 2 == 0}

P_A=len(A) / len(omega)
```


inny przykład
$\Omega = \{1,2,3,4,5,6\}$
$n = 6$
$B=\{5,6\}$ zdarzenia pojegające na wyrzuceniu liczby większej niż 4
$\#B=2$
$P(B) = \frac{2}{6}=\frac{1}{3}$

```py
omega = {1,2,3,4,5,6}
B ={item for item in omega if item > 4}

P_B = len(B)/len(omega)

```
