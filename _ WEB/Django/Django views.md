
>[!definition]
>**views** are Python functions which take a URL request as parameter and return an HTTP respons or throw an exception like 404
>



Each view need to be mapped to a corresponding URL pattern. This is done via a Python module called URLConf(URL configuration) (in the avriable `ROOT_URLCONF` in the Django project value by defaul is `MyProject.urls` (*MyProject* is a name of the Django project )

---
Every Django app should have its own `URLConf`. This modyle needs to be included in the root `URLConf module`   

**the root URLConf** module:
```python 
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
	path('admin/', admin.site.urls),
	path('', include('books.urls')),
]

```
This tells Django to search for URL patterns in the file `books/urls.py`
-> [[Django include]]


so
`books/urls.py` should look like:
```python
from django.urls import path
from . import views

urlpatterns = [
	path('books/<int:pk>/', views.book_detail),
	path('books/<str:genre>/', views.books_by_genre),
	path('books/', views.book_index),
]

```

`path('books/<str:genre>/', view.books_by_genre)` if it will be a URL request `/book/crime/`, Django will call the function `views.books_by_genre(request, genre = "crime")`

**Path convertors**:
The following path convertor types are available in Django
- `int` – Matches zero or any positive integer.
- `str` – Matches any non-empty string, excluding the path separator(‘/’).
- `slug` – Matches any slug string, i.e. a string consisting of alphabets, digits, hyphen and under score.
- `path` – Matches any non-empty string including the path separator(‘/’)
- `uuid` – Matches a UUID(universal unique identifier).
















