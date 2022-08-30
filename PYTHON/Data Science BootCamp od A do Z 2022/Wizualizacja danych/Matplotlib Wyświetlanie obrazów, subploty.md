[[0-Matplotlib wprowadzenie]]
#python/matplotlib 


```py
import matplotlib.pyplot as plt
import matplotlib.image as mpimg

# w zmiennej img przechowamy nasz obraz 'office,jpg'
# dostanemy obiekt typu numpy.ndarray
img = mpimg.imread('office.jpg')

# (wysokość, szerokość, ilość kolorów)
img.shape
(680, 1024, 3)

# wyświetlamy nasz obraz
# wyłączamy axis
plt.imshow(img)
plt.axis('Off')
```

siatka obrazów
```py
fig = plt.figure(figsize=(12,10))
plt.subplot(221)
plt.imshow(mpimg.imread('office.jpg'))
plt.subplot(222)
plt.imshow(mpimg.imread('business.jfif'))
plt.subplot(223)
plt.imshow(mpimg.imread('children.jfif'))
plt.subplot(224)
plt.imshow(mpimg.imread('workplace.jpg'))
```

![[siatka_obrazow.png]]

Wersja krótsza:
```py
fig = plt.figure(figsize=(12,10))

for idx, img in enumerate(['office.jpg', 'business.jfif', 'children.jfif', 'workplace.jpg']):

 plt.subplot(220 + idx + 1)
 plt.imshow(mpimg.imread(img))
```














