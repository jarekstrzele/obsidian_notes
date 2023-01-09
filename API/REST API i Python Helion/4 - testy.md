[[_ 0 start REST API i python]]


---
# Testy
#python/tests

Testy są bardzo ważne!!!
Minimum to pokrycie całego kodu testami jednostkowymi.

Musimy zainstalować bibliotekę ==pytest==
#pytest 
`pip3 install pytest`

teraz w projekcie tworzymy nowy folder `test` a wszystkie pliki w tym folderze muszą zaczynać się od słowa `test`!!! więc test dla pliku `main.py` będzie nazywał się `test_main.py` itd.
nagłówek pliku testowego:

```python
from fastapi.testclient import TestClient
from main import app

client = TestClient(app)
```

dopisujemy pierwszą metodą testująca docs
na stronie `/docs` jest 
`<title>FastAPI - Swagger UI</title>`
```python
def test_read_docs():
    response = client.get("/docs")
    assert response.status_code == 200
    assert "<title>FastAPI - Swagger UI</title>" in response.text

```

aby uruchomić test w terminalu piszemy:
`pytest`

Unittesty powinny być niezależne od innych komponentów systemu, więc chcąc przetestować pierwszy endpoint musimy zamockować bazę danych
więc
w pliku testowym dopisujemy
```python
from unittest.mock import Mock, patch

def test_users_all():
	
```






