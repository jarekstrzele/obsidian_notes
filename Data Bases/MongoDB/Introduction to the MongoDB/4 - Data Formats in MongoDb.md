[[_ Intro to MongoDB]]

---

# Data  formats in MongoDB
por. [[Learn JSON in 10 minuts]]

## JSON
#json 
usually is a string because is used to data exchange
```json
'{
	"type":"Phone",
	"price": 120.
	"inStock": true,
	"features": [
		"HD Camers", "Wifi"
		]
}'
```

==data types==
- string
- number
- object
- array
- boolean
- null

DOUBLE QUOTES

## JSON vs JS Object

JSON | JS Object
---| ---
string | data type
keys ==have== to be in double quotes | keys ==may== be in double quotes
conversion to <br> JS Object <br>`JSON.parse()` | conversion to<br> JSON <br> `JSON.stringify()`


----
## BSON format
#bson
all documents in the MongoDB database are stored using BSON format

>[!BSON]
>Binary JSON
>Hex

'w' -> ASCII $119$ -> Hex $77$

**BSON** supports more the 6 data type


## Extended JSON
#extended_json

Extended JSON is used to represent BSON data types

`ObjectId("43095834vncr39845")`
`NumberLong(323423)`
`ISODate("2018-06-09To:44:33:000Z")`

## Most common BSON types in Extended JSON
BSON type | Type ID | Extended JSON repr
---| :---: | --- 
String | 2 | "Sample sting"
Object | 3 | {"type": "Phone", "price":120}
Boolean| 8 | true
Array | 4 | [10,15]
Double | 1 | 10.5
32-bit integer | 16 | NumberInt(150)
ObjectId | 7 | ObjectId("32452wggrt3452342")
Date | 9 | ISODate("2018-07-15T15:33:33.732z")













