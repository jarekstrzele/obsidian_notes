
## FIRST Version
```python
from tkinter import *
# Define window
root=Tk()
root.title("Weather Forecast")
root.iconbitmap('weather.ico')
root.geometry('400x400')
root.resizable(0,0)

# define fonts and colors
sky_color = '#76c3ef'
grass_color = '#aad207'
output_color = '#dcf0fb'
input_color = '#ecf2ae'
large_font = ('SimSun', 14)
small_font = ('SimSun', 10)

# define functions
  

# define layout

# create frames
sky_frame = Frame(root, bg=sky_color, height=250)
grass_frame = Frame(root, bg=grass_color)
sky_frame.pack(fill=BOTH, expand=True)
grass_frame.pack(fill=BOTH, expand=True)

output_frame = LabelFrame(sky_frame, bg=output_color, width=325, height=225)
input_frame = LabelFrame(grass_frame, bg=input_color, width=325)
output_frame.pack(pady=30)
output_frame.pack_propagate(0)
input_frame.pack(pady=15)

  

# Output frame layout
city_info_lbl = Label(output_frame, bg=output_color, text="Testing")
weather_lbl = Label(output_frame, bg=output_color, text="Testing weather")
temp_lbl = Label(output_frame, bg=output_color, text="Testing temp")
feels_lbl = Label(output_frame, bg=output_color, text="Testing feels")
temp_min_lbl = Label(output_frame, bg=output_color, text="Testing min ")
temp_max_lbl = Label(output_frame, bg=output_color, text="Testing  max ")
humidity_lbl = Label(output_frame, bg=output_color, text="Testing humi ")
photo_lbl = Label(output_frame, bg=output_color, text="Testing photo")

city_info_lbl.pack(pady=8)
weather_lbl.pack()
temp_lbl.pack()
feels_lbl.pack()
temp_min_lbl.pack()
temp_max_lbl.pack()
humidity_lbl.pack()
photo_lbl.pack(pady=8)

# input frame layout

#create  input frame btn and entry
city_entry = Entry(input_frame, width=20, font=large_font)
submit_btn = Button(input_frame, text="Submit", font=large_font, bg=input_color)

search_method = IntVar()
search_method.set(1)
search_city = Radiobutton(input_frame, text='Search by city name', variable=search_method, value=1, font=small_font,bg=input_color)
search_zip = Radiobutton(input_frame, text='Search by zipcode', variable=search_method, value=2, font=small_font, bg=input_color)

city_entry.grid(row=0, column=0, padx=10, pady=(10,0))
submit_btn.grid(row=0, column=1, padx=10, pady=(10,0))
search_city.grid(row=1, column=0, pady=2)
search_zip.grid(row=1, column=1, padx=(0,10), pady=2)
  

root.mainloop()
```


# How to get API key?
https://openweathermap.org/api

make an account: jsdydaktyk@gmail.com
make your own api key 


look to the doc *current weather data* to see how to select by city, by zip

> you will need `pip install requests`

```python
# define functions
def search():
    """Use open weather api to look up current weather conditions given a city, country"""
    global response

    # get API repsonse
    url = 'https://https://api.openweathermap.org/data/2.5/weather'
    api_key = 'dda71caf405d01b0091c6ff97588f0b0'

    # search by the appropriate query, either city name ot zip
    if search_method.get() == 1:
        querystring = {'q':city_entry.get(), 'appid':api_key}
    elif search_method.get() == 2:
        querystring = {'zip':city_entry.get(), 'appid':api_key}}
        
```







