[[_ Intro Scalable Web Applications with Python, Flask and SQLAlchemy]]

[[routing in flask]]


---

# SECTION 3  Jinja 2 TEMPLATING
#pythpn/jinja

==Jinja2== is a template engine for python
https://palletsprojects.com/p/jinja/

>` {% logic %}`
> `{{ variable }}`


```py
@app.route('/watch')
def top_movies():
    movie_list = [ 'autopsy of jane doe',
                   'neon demon',
                   'ghost in a shell',
                   'kong: skull island',
                   'john wick 2',
                   'spiderman - homecoming']
                   
    return render_template('movies.html',
					        movies=movie_list,
                            name='Harry')
```

```html
...
<ul>
  {% for item in movies %}
   <li> the  movie: {{ item }} </li>

  {% endfor %}

</ul>
...
```

if, elif
```html 
{% if length < 2 %}
    <td>short  </td>
{% elif length >= 2 and length <=3 %}
    <td> medium </td>
{% else %}
    <td style="color: red"> long </td>
{% endif %}

```

__METHOD__ `url_for`

`url_for(folder_name, css_file_name)`

__traditionale way__
`<link rel="stylesheet" href="static/css/style.css">`

__with `url_for` method__
` <link rel="stylesheet" href="{{ url_for('static', filename='css/style.css')}}"> `


---
## filters
Using digial filters, we can modify the values of the variables that we pass into the e-mail files

`{{ variable | filter | filter }}`

```html
  <!-- dictsort -sortowanie
            false - case-insensitive
            value sort by value
        -->
{% for movie, duration in movies | dictsort (false, 'value') %}
            
	<li> {{ movie | title }} : {{ duration |round(1) }} </li>
          
{% endfor %}

```

```html
    <ol type="1">
        <li> default value : {{ name | default('value not defined', ture)}} </li> <br>

        <li> capital case : {{ film | capitalize }} </li> <br>
        <li> length : {{ movies | length }} </li> <br>
        <li> first itme : {{ movies | first }} </li> <br>
        <li> make a list : {{ film | list }} </li> <br>
        <li> capital case : {{ film | replace('carol', 'cookie') | upper }} </li> <br>
    
    
    </ol>
```



---


## MACRO




## MACROS  
macro.html
```py

      {% macro render_dict(dictionary) %}
      {% for key, val in dictionary.items() %}
      <tr><td>{{ key }}</td><td>{{ val }}</td>
      {% if val<=2 %}<td>short</td>
      {% elif val >=2 and val <=3 %} <td>medium</td> 
      {% else %}<td style="...">long</td>
      {% endif %}</tr>
      {% endfor %}  
```

using_macro.html
```html
{% import 'macros.html' as my_macros %}
<html>
        <head>
                <meta charset="UTF-8">
                <title> dictionary</title>
        </head>
        <body>
            {{my_macros.render_dict(movies)}}
        </body>
</html>
```




[[ORM]]
[[PYTHON/Lear_Build_Flask/Git]]

---

  