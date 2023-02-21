#python #json #w3school 

# Python JSOn
**JSON** is a syntax for storing and exchanging data.
**JSON** is text, written with JavaScript object notation

#### `import json`

#### From JSON to Python
json - `json.loads()` -> python dict
```python
# some JSON
x = '{ "name": "John", "age": 30, "city":"New york"}'

# parse
y = json.loads(x)

print(type(y)) # -> dict

```


#### From Python to JSON

##### `json.dumps()` to convert Python primitive types into JSON equivalent

python object  - `json.dumps()` -> json
```python
# a Python object dict
x = { "name": "John", "age":30, "city": "New York"}

# convert
y = json.dumps(x)

print(y) # a JSON string

```


you can convert Python objects of the following types:
Python object | JSON
---| ---
dict | object
list| array
tuple | array
str | string
int | number
float |number
True | true
False | flase
None | null


###### intend 
is a parameter of `dumps()` function
`print(json.dumps(x, indent=4)`
###### separators
default value `separators=(", ",": "`
`, ` separates each object
`: ` seperates keys from values

###### sort_keys
to order the keys
`sort_keys=False`
`sort_keys=True`

`json.dumps(x, intend=4, separators=". ", " = ", sort_keys=True`

##### `json.dump()` to encode and write JSON data to a file

`json.dump(dictionary, file, others)`
others:
the same as in `json.dumps`









