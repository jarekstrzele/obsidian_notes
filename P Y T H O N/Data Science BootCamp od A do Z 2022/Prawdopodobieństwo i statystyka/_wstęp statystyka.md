[[]]


---

# Wstęp



## Lekkie wprowadzenie

[[zmienna losowa]]


---

# Statystyka opisowa

## Miary tendencji centralnej

[[średnia arytmetyczna]]na
[[Mediana]]
[[Moda Dominanta Watość modalna]]

---

## MIARA ROZRZUTU
[[średni błąd]]
[[Wariancja ciągu]]
[[Odchylenie standardowe]]


---

[[Dystrybuanta empiryczna]]


[[przestrzeń probabilistyczna]]

#przestrzen_probabilistyczna 
## przestrzeń probabilistyczna 







---

## NIEZALEŻNOŚĆ zdarzeń

Dwa zdarzenia $A$ i $B$ są niezależne, gdy:
$$
P(A \cap B) = P(A)*P(B)
$$
Prawdopodobieństwo iloczynu jest równe iloczynowi prawdopodobieństw.

zdarzenia $A$ i $B$
$A=\{2,4,6\}$
$B=\{5,6\}$

```py

omega = {1,2,3,4,5,6}
intersection_AB = set.intersection(A, B)
P_intersection_AB = len(intersection_AB)/len(omega)

P_A=len(A) / len(omega)
P_B=len(B) / len(omega)
PA_PB = P_A * P_B

check = "zdarzenia niezależne" if PA_PB == P_intersection_AB else "zdarzenia zależne"


```
-> "zdarzenia niezależne"

zmiana B na zdarzenia większe od 3
`B={ item for item in omega if item >3}`

-> "Zdarzenia zależne" , bo przez zdarzenie $A$ wpływamy na $B$

 - - - - - - - 

Wyrzucenie oczek większą niż jeden
`C={item for item imega if item >1}`

=> A i C są zdarzeniami zależnymi

> Dwie zmienne są niezależne, jeżeli wszystkie zbiory są niezależne


---

## Prawdopodobieństwo warunkowe
Prawdopodobieństwem warunkowym zdarzenia $A$ pod warunkiem zajścia zdarzenia $B$ przy założeniu, że $P(B)>0$ nazywamy:
$$
P(A|B)=\frac{P(A \cap B)}{P(B)}
$$

`A: {2,4,6}`
`B: {5,6}`
`przecięcie A i B: {6}`
`PA_cond_B = P_intersection_AB/ P_B`














