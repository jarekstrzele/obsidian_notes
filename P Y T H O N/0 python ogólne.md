# Wirtualne środowisko
#python/virtual

==tworzenie:==
`python3 -m venv nazwa_srodowiska`

==aktywacja==
`source nazwa_srodowiska/bin/activate`

w windowsie
` .\nazwa_srodowiska\Scripts\activate.bat`

==deaktywacja==
`deactivate`

source ~/PROG/env_bill/bin/activate


---
inne rozwiązania
__Conda__
__Pipenv__

---

# zatrzymywanie serwera
#python/flask
```
Sudo systemctl restart flask-server

Or sudo systemctl restart nginx

Or sudo systemctl restart apache

```

# flask

```
if __name__ == '__main__':
      app.run(host='0.0.0.0', port=80)
```
---







