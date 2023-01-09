# Learn JSON in 10 Minutes
https://www.youtube.com/watch?v=iiADhChRriM

## What is JSON?
JavaScript Object Notation
- data representation format
- Commonly Used for APIs and Configs
- lightweight and easy to read/write
- integrates easily with most languages (to parse JSON strings into objects or classes in tha language)

## JSON Types
- strings ``"hello"`
- numbers `10  1.5  -30  1.2e10`
- booleans `true false`
- null `null`
- arrays `[1,2,3] ["hey", "world"]`
- object `{"key":"value"}  {"age":20}`


## example
`user.json`:
```json
{
	"key":"value",
	"name":"Kyle",
	"number" :3,
	"isProgrammer": true,
	"hobbies": ["weight lifting", "Bowling"],
	"friends": [{
		"name":"Joey",
		"favoriteNumber": 100,
		"isProgrammer": false,
		"friends": []
	}
	]
}
```

`companies.json`
```
[
	{
		"name": "Big Corp"
		"numberOfEmployee": 10000,
		"ceo" : "Mary",
		"rating": 3.6
	},
	
	{
		"name": "Samll StartUp"
		"numberOfEmployee": 3,
		"ceo" : null,
		"rating": 4.6
	},
	
]
```

`JSON.parse(jsonFile)` --> javascript object and access by `[index]`

