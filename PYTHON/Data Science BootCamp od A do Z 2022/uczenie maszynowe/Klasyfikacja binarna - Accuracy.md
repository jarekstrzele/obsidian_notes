[[_ Klasyfikacja binarna]]

---
## Accuracy dokładność klasyfikacji
$$
Accuracy = \frac{correct-prediction}{total-prediction}*100
$$
tego typu metryki pomagają nam ocenić, czy model dobrze przewiduje

```python
from sklearn.metrics import accuracy_score
```

tworzymy przykładowe dane (`true` te prawdziwe, `pred` te przewidziane przez model)
```python
y_true = np.array([1,0,1,1,0,1,1,0,1,0,1,1,0,1,1,0,1,1,0,1,1,1,0,1,1,0,1,1,0,1])
y_pred = np.array([0,0,1,1,0,1,0,0,1,1,0,1,0,1,1,0,0,1,0,1,1,1,1,1,1,0,1,1,0,1])

accuracy_score(y_true, y_pred)
```

z tych danych tworzymy obiekt `dataframe` z pandas
```python
result = pd.DataFrame({'y_true':y_true, 'y_pred':y_pred})
result
```
pozwoli to nam na wizualizację w plotlib
więc
sortujemy dane po kolumnie `y_true`
`result = result.sort_values(by='y_true')`

dodamy nową kolumnę `sample`, aby wiedzieć, w której próbce popełniliśmy błąd
lecz
najpierw porządkujemy index, bo po sortowaniu jest tam bałagan `result = result.reset_index(drop=True)`
teraz dodajmy kolumnę: `result['sample']=result.index + 1`

teraz robimy wykresy:
```python
fig = make_subplots(rows=2, cols=1)

fig.add_trace(go.Scatter(x=result['sample'],y=result['y_true'], mode='markers', name='y_true'), row=1,col=1)

fig.add_trace(go.Scatter(x=result['sample'],y=result['y_pred'], mode='markers', name='y_pred'), row=2,col=1)

fig.update_layout(width=900, height=500, title="klasyfikator binarny")

fig.show()

```


![[images/klasyfikator_binarny.png]]