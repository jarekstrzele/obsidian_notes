
[[0-NumPy wprowadzenie]]
[[Numpy macierze]]
[[Numpy rozwiązywanie równanń]]

## wektor

v = [v1, v2]
**norma wektora, długość wektora w R<sup>2</sup>**
$$
||v||=\sqrt{v_1^2 + v_2^2}
$$


```py
v1 = np.array([0,4])

np.linalg.norm(v1) # liczy długość wektora

```

ugólnienie:
$$
||v||=\sqrt{v_1^2 + v_2^2 + ... + v_n^2}
$$
```py
v1 = np.array([0,4])

np.linalg.norm(v1) # liczy długość wektora
```


**odległość dwóch punktów na płaszczyźnie** R<sup>n</sup>
$$
d(p,p) = d(q,p) = \sqrt{(q_1-p_1)^2 + (q_2-p_2)^2 + ... +    (q_n-p_n)^2 } = \sqrt{\sum_{i=1}^n(q_i-p_i)^2}
$$
```py
p = np.array([3,0])
q = np.array([0,4])

np.linalg.norm(p - q)
```

[[Numpy macierze]]



