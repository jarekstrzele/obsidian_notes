#api #python 
[[_ 0 100 Days of Code 2023]]


>[!info] API
>Application Programming Interface is a SET of:
>- commands
>- functions
>- protocols
>- objects
>
that the programmer can use to
> - create software or 
> - interact with an external system

> API is an **interface** or a sort of **barrier** between your *programm* and *external system*.

![[API.excalidraw | 500 ]] 



>[!info] API endpoint
>- You can think that  endpoints are a location.
>- you want some data, so you have to know where this data are store
>-  e.g. `api.coinbase.com`

# Request
If you know an API endpoint to have to make a request 
	like a teller in the bank"
		you ask him/her about money and he/she gives you money controling that process


EXAMPLE:
http://open-notify.org/Open-Notify-API/ISS-Location-Now/
```json
javascript
{
  "message": "success", 
  "timestamp": UNIX_TIME_STAMP, 
  "iss_position": {
    "latitude": CURRENT_LATITUDE, 
    "longitude": CURRENT_LONGITUDE
  }
}
```

you can write into the browser http://api.open-notify.org/iss-now.json and you get:
`{"message": "success", "timestamp": 1672319872, "iss_position": {"latitude": "45.0201", "longitude": "-156.2389"}}`

add to chrom # JSON Viewer Pro
#plugin #json #chrome 

http://open-notify.org/Open-Notify-API/ISS-Location-Now

```python
import requests

response = requests.get(url="http://api.open-notify.org/iss-now.json")

print(response) # -> <Response [200]>
```

```python
import requests

response = requests.get(url="http://api.open-notify.org/iss-now.json")

response.raise_for_status()

data = response.json()
long = data["iss_position"]["longitude"]
lat = data["iss_position"]["latitude"]

iss_position = (long, lat)
print(iss_position)
```

>Metoda `raise_for_status()` jest używana do sprawdzenia statusu odpowiedzi HTTP wysłanej przez serwer. Jeśli status odpowiedzi jest różny od 200 (czyli OK), wówczas funkcja wygeneruje wyjątek, który opisuje błąd. Ta metoda pozwala na łatwe i szybkie przetworzenie błędów związanych z połączeniem z serwerem i uzyskaniem odpowiedzi HTTP. W takim przypadku, nie musisz ręcznie sprawdzać kodu statusu odpowiedzi i wywoływać wyjątku, jeśli jest on nieprawidłowy - ta metoda to robi automatycznie.

https://www.latlong.net/Show-Latitude-Longitude.html

---
# Kany api
```python
from tkinter import *

import requests

def get_quote():
    res = requests.get(url="https://api.kanye.rest")
    res.raise_for_status()

	data = res.json()

    canvas.itemconfig(quote_text, text=data["quote"])

window = Tk()
window.title("Kanye Says...")
window.config(padx=50, pady=50)

canvas = Canvas(width=300, height=414)
background_img = PhotoImage(file="background.png")
canvas.create_image(150, 207, image=background_img)

quote_text = canvas.create_text(150, 207, text="Kanye Quote Goes HERE", width=250, font=("Arial", 30, "bold"), fill="white")
canvas.grid(row=0, column=0)

kanye_img = PhotoImage(file="kanye.png")
kanye_button = Button(image=kanye_img, highlightthickness=0, command=get_quote)
kanye_button.grid(row=1, column=0)


window.mainloop()
```

you need two images.

----
# API parameters
They allows you to give an input when you are making your API request

## Sunset and sunrise times API
https://sunrise-sunset.org/api

this is an endpoint: https://api.sunrise-sunset.org/json
`endpoint?param1Name=value&param2Name=value`

`https://api.sunrise-sunset.org/json?lat=21.23123&lng=-3.3424543`

```python
import requests
from datetime import datetime

MY_LAT = 53.849500
MY_LONG = 20.591050

parameters = {
    "lat": MY_LAT,
    "lng": MY_LONG,
    "formatted":0
}

response = requests.get(url="https://api.sunrise-sunset.org/json", params=parameters)
response.raise_for_status()

data = response.json()
sunrise = data["results"]["sunrise"].split("T")[1].split(":")[0]
sunset = data["results"]["sunset"].split("T")[1].split(":")[0]
time_now=datetime.now().hour

print(sunrise, sunset, time_now)
```

```python
import requests
from datetime import datetime
import smtplib # sending email
import time

MY_EMAIL = "eee@gmail.com"
MY_PASSWORD = "eewwe"
MY_LAT = 53.849500
MY_LONG = 20.591050


def is_iss_overhead():
    response = requests.get(url="http://api.open-notify.org/iss-now.json")
    response.raise_for_status()
    data = response.json()
    iss_long = float(data["iss_position"]["longitude"])
    iss_lat = float(data["iss_position"]["latitude"])
    if MY_LAT-5 <= iss_lat <= MY_LAT+5 and  MY_LONG-5 <= iss_long <= MY_LONG+5:
        return True
    else:
        return False


def is_night():
    parameters = {
        "lat": MY_LAT,
        "lng": MY_LONG,
        "formatted":0
    }

    response = requests.get(url="https://api.sunrise-sunset.org/json", params=parameters)
    response.raise_for_status()
    data = response.json()
    sunrise = int(data["results"]["sunrise"].split("T")[1].split(":")[0])
    sunset = int(data["results"]["sunset"].split("T")[1].split(":")[0])
    time_now=datetime.now().hour

    if time_now >= sunset or time_now <= sunrise:
        return True
    else:
        return False


while True:
    time.sleep(60)
    if is_iss_overhead and is_night:
        connection = smtplib.SMTP("smtp.gmai.com")
        connection.starttls()
        connection.login(MY_EMAIL, MY_PASSWORD)
        connection.sendmail(
            from_addr=MY_EMAIL,
            to_addrs=MY_EMAIL,
            msg="Subject:Look up \n\n The ISS is above you in the sky."
        )
```



