#python 

# Section 15
==SCOPE (as 1 first it is searched, 4 as last it is searched)==

1.  ==local==   names assigned in any way within a function (`def` or `lambda`) and not declared global in that function  
2. ==enclosing== function locals EFLs  ; name in the local scope of any and all enclosing functions (`def` or `lambda`), from inner to outer  
 3.  ==globale==   names assigned at the top-level of a module file or declared global in a def within the file  
 4. ==built-in==

```python
x = 25             # global        

def my_func():  
      x = 50      # local  
      return x  

print(x)              # ->      25 # global x  
print(my_func())      # ->      50 # local  x  
print(x)              # ->      25 # global x

```

```python
lambda x: x**2      # x is local scope  
name = "this is a global name"  

def greet():  
	name = "sammy"  

    def hello():  
        print("hello " + name)  

    hello()  

greet() # -> nothing    def greet() without last line ' hello() '
greet() # -> hello sammy
greet() # -> hello this is a global name # if we delete a line inside the def 'name="sammy"

```

```python
x = 50  

def f(x):  
	x =100  
    print(x)  

f(x)     # -> 100      # local x
print(x) # -> 50       # global x

```

```py

x = 50  
def f(x):  
	global x = 100  
    print(x)  

f(x)     # -> 100   # global x
print(x) # -> 100   # global x
```


## OOP
`type(arg)      ->      <type of arg>  `
`type(20.0)    ->      <class 'float'>`

```python
class Sample():  

      pass  

x = Sample()  
print(type(x))      # ->      <class '__main__.Sample'>
```

```python
class Dog():  

	  # class Object Attribut  
      species = "mammal"  

	  def __init__(self, breed, name):  
            self.breed = breed  
            self.name = name  

	  
mydog = Dog(breed = "Lab", name = 'Smamy')  
print(mydog.breed)       # ->      Lab  
print(mydog.species)     # ->      mammal
```

# Errors and Exceptions
#python/errors_and_exceptions

>I make a mistake (e.**g. print('hell),** and I get an error message: "SyntaxError: EOL while scanning string literal"  this type of error is an example of EXCEPTION)  

```python
try:  
      you do your operations..   
except except1:  
      if there is excep1, then execute this block  
except except2:  
      if there is excep2, then execute this block  
else:  
      if there is no exception then execute this block  
finally:  
      comp do this always  
```
  
---
  
# regular expressions 
```python
import re  

# match = re.search(patterm, text)
# => returns a special match object  
# type(match) => <class 're.Match'>  
# match.start() => return the first index number of matchingtext

split_term = '@'  
email = 'user@gmail.com'  
print(re.split(split_term, email)) # =>  ['user', 'gmail.com']  

# re.findall()  -> returns a list of all not verlapping matches in the string  
print(re.findall('match', 'text then match or it not match')) 
# => ['match', 'match']  
```

`*`      zero or more  
`d*`    'd' won't be  or will be  more  

`+`      one or more  
`d+`    'd' will be one or more  

`?`      zero or one  
`d?`    'd' will be one or zero  

`{n}`        n times  
`d{3}`      'd' will be three times  
`d{1,3}`   'd' 1 or 2 or 3  

 `s[sd]+`    s followd by one or more S or one or more d  

`^`                to exclude terms  
`[^!.?]+ `   exclude one or more !, . , ?  

```py
t_phrase = 'This is. This? Mo!!!'  
t_paterrn = ['[^!.?]+']  

# =>  ['This is', ' This', ' Mo']  
```

`[a-z]+`  

`[A-Z]+ ` 

`r' \d+'`      one or more digit   

`\D `           no digit  

`\s  `          wihte space  

`\w`            alphanumeric  

`\W `           no alphanumeric  

  
---
# MODULE and  PACKAGES  
`import module_name  
`module_name.func_inside()  

`import module as mm  
`mm.func()  

`from module import fun  
`func()  

---
# DECORATERS  
**DECORATOR**     is a function that modies the functionality  of another func  

*locals()*        returns a dictionary of locals variables  
*globals()*      return a dictionary of global variables  

```python
def new_deco(func):  

	def wrapper():  
		print("Wrapper started. A function will be executed")  
	
	func()  
    print("end of the function")  
	
	return wrapper  


def hello():  
	print("Jestem funkcją hello")  
	print('po prostu hello')  

hello()  

x = new_deco(hello)  
print('Wykonam funkcję x()')  
# x()  
print('dekoruję hello()')  
hello = new_deco(hello)  
hello()   
```
---
mysterious line of code:  

` if __name__ == "__main__"  

Sometimes when you are importing from a module, you would like to know whether a modules function is being used as an import, or if you are using the original. .py file of that module  

if I run file directly ` __name__ == __main__  
so  
when I import this file, `__name__ is not __main__` 
```python
if __name__ == "__main__":  
      # logic of the file is here  
      # this will be executed directly

```








