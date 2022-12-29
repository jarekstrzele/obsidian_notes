#api #python 

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

## Request
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

http://open-notify.org/Open-Notify-API/ISS-Location-Now/
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


https://www.latlong.net/Show-Latitude-Longitude.html







