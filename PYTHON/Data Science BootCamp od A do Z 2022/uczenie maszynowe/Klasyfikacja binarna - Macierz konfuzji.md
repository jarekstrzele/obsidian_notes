[[_ Klasyfikacja binarna]]

---

# Macierz konfuzji
```python
from sklearn.metrics import confusion_matrix
confusion_matrix(y_true, y_pred)

# array([[ 8, 2], [ 4, 16]])
# problem jest binarny, więc macierz jest dwa na dea
```
cel: maksymalizacja na przekątnej

wizualizacja
```python
import plotly.figure_factory as ff
from sklearn.metrics import confusion_matrix

y_true = np.array([1,0,1,1,0,1,1,0,1,0,1,1,0,1,1,0,1,1,0,1,1,1,0,1,1,0,1,1,0,1])

y_pred = np.array([0,0,1,1,0,1,0,0,1,1,0,1,0,1,1,0,0,1,0,1,1,1,1,1,1,0,1,1,0,1]) 

def plot_confusion_matrix(cm):
	cm = cm[::-1]
	cm = pd.DataFrame(cm, columns=["pred_0", "pred_1"], index=["true_1", "true_0"])
		fig = ff.create_annotated_heatmap(z=cm.values, x=list(cm.columns), y=list(cm.index), colorscale="ice", showscale=True, reversescale=True)
	   
 fig.update_layout(width=400,height=400, title='Confusuin Matrix', font_size=16)

  fig.show()

  
cm = confusion_matrix(y_true, y_pred)
plot_confusion_matrix(cm)
```

![[images/confusion_matrix.png]]

```python
tn, fp, fn, tp = cm.ravel()

print(f'TN - True Negative: {tn}')
print(f'FP - False Positive: {fp}')
print(f'FN - False Negative: {fn}')
print(f'TP - True Positive: {tp}')

# TN - True Negative: 8 
# FP - False Positive: 2 
# FN - False Negative: 4 
# TP - True Positive: 16

# 0 negative
# 1 positive
# np. '4' błędnie przewidziana 'pred_0' czyli klasa negatywna
```


