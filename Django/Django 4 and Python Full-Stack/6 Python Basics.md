[[_ 0 Django 4]]

-------
# Python Basics
in termianl (`cmd`, `Power Shell`, ....):
`python file_name.py```

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





















