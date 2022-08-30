[[_ Deep Dive INTRO]]
[[Scopes, closures, Decorators]]


[[Decorator Application (Class Decorator )]]
[[Decorator Application (Class Decorator ) CODE]]

---
# Decorator Application (Dispatching)

*dispatch* - wysyłać coś do kogoś
*dispatching* wysyłka

## Single Dispatch Generic Functions
[[html module]]

first step:
```python
from html import escape

def html_escape(arg):
  return escape(str(arg))

def html_int(a):
  return '{0} (<i>{1}</i>'.format(a, str(hex(a)))

def html_real(a):
  return '{0:.2f}'.fomrat(round(a,2))

def html_str(s):
  return html_escape(s).replace('\n','<br>\n' )

def html_list(l):
  items = ('<li> {0} </li>'.format(html_escape(item)) for item in l )
  return '<ul>\n' + '\n'.join(items) + '\n</ul>'


def html_dict(d):
  items = ('<li> {0}={1} </li>'.format(k, v) for k, v in d.items())
  return '<ul>\n' + '\n'.join(items) + '\n</ul>'


```

and now a dispaching function:
```python
def htmlize(arg):
  registry = {
      object: html_escape,
      int: html_int,
      float: html_real,
      str: html_str,
      list: html_list,
      tuple: html_list,
      dict: html_dict
   }
  
  fn = registry.get(type(arg), registry[object])

  return fn(arg)
```





