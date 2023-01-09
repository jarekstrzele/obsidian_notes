[[_ 0 Django 4]]

-------
# Python Basics
in termianl (`cmd`, `Power Shell`, ....):
`python file_name.py`

## variables
`variable_name = value`
```python
podatek = 0.1
dochod = 100
print(podatek*dochod)
```


## string
- is used to hold text inforamtion and are indicated with `''` or `""`
- is a sequence of characters (there is an order to the string)
`"abscdf"` `'absc'`

### slicing string
`"abcd[:2]"` -> `ab`
`"abcd[1:2]"` -> `b`

### indexing
`"abcd"[0]` -> `a`

### method
`"12xc".capitalize()`
`"12xc".upper()`
```python
some_text = "This is some text"
print(some_text.split()) #-> ['This', 'is', 'some', 'text']

some_text = "This is -- some text"
print(some_text.split("--")) #->['This is ', ' some text']

print(some_text[1])#->h
print(some_text[-2])#->x

x = "first"
y = "second"
print(x+y) #->firstsecond

print(f"this is {x}") #->this is first



```

# list
`a = ['12', 13, true, ["second list"]]`
list is a squence of items
`a[2] #->true`
`a[1:3]#->[13, true]`
to add an item to a list: `list_name.append(new_item)`
to insert an item: `list_name.insert(<index>, <what>)`; `some_list.insert(2, "newItem")`
to remove an item" `some_list.pop()` the last item will be removed and returned; `some_list.pop(<index>)`
to reverse a list: `some_list.reverse()`
to sort: `some_list.sort()`

# dictionary
`{key:value}`
```python
employees = {"chef":"Amy", "ceo":"Jason"}

print(employees["ceo"]) #->Amy
employees["waiter"] = "Mike" # add a new item to the dict
employees["chef"] = "Jose" # Update a value of key "chef"

# {<immutable_key> : <mutable or immutable value>}

print(employees.keys()) # returns all keys
print(employees.values()) # returns all values 
print(employees.items()) # returns all key-value pairs

```

# tuple
It is like a list but it is immutable (can not be changed/mutated)
Functions often return tuples as results (`a_dic.items()` -returns->tuple)


## Boolean
`True`, `False`
`some_value < some_value`
`>`, `<`,`<=`,`>=`,`==`,`!=`
`or`, `and`

# Flow control
```
if <condition>:
	<make_something>
elif <condition>:
	<make_something>
else:
	<make_something>
```

## For loops
*iterable* means you can "iterate" over the object
you can iterate over every character in a string, every item in a list, every key in a dict ....
```python
my_iterable = [1,2,3]
for item in my_iterable:
	print(item)
```

```python
for my_key in my_dict:
	print(my_key)

for my_key, my_value in my_dict.items():
	print(my_key, my_value)
```


## While loops
```python
while <some_boolean_condition>:
	# do something
```

while forever:
```python
while True:
	print("While forever")
```


## Functions
We can use functions to have a repeat use block code to easily execute

```python
def function_name():
	''' docstring explains function ```
	# do something
	print("Hej")

```

```python
def function_name(arg):
	''' docstring explains function ```
	# do something
	print(f"Hej, {arg}")

```

```python
def function_name(ar1, ar2):
	''' docstring explains function ```
	# do something
	
	return a1+ar2

```

`function_name()` you call that function

```python
mylist=[1,2,5,3,1,6,7,2]

def checker(list_to_check):
	for num in list_to_check:
		if num == 10:
			return True

	return False

print(checker(mylist)) #-> False
```




















