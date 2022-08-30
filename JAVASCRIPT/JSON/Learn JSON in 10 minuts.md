
# Learn JSON in 10 minuts
#json   #web_dev_simplified #youtube


https://www.youtube.com/watch?v=iiADhChRriM&list=PLZlA0Gpn_vH85jM1TWO6TdCtSr6ruglWn

==JavaScript Object Notation==
- data representation format
- commonly used for APIs and Congis
- lightweight abd easy to read/write
- integrates easily with most languages


## JSON Types
- String     ``"Hello WOrld" "i"``
- Numbers `10 1.5 -30 1.2e10`
- Booleans t`rue false`
- null `null`
- Arrays `[1,2,3], ["helo", "aa"]`
- Object `{"key":"value" } { "age":30}`

----
## FILE `user.json`
```json
{
	"name": "kyle",
	"favoriteNumber": 3,
	"isProgrammer": true,
	"hobbies": ["Weight lifting", "Bowling"],
	"friends": [{
		"name": "Joey",
		"favoriteNumber": 100,
		"isProgrammer": false,
		"friends": [ ....]
	}]
}
```

Quite often we use 'json' as a text,
so us \` a json content  \`  
and then use `JSON.parse(variable_name_with_this_text)` -> `json`

```javascript
let companies = `[
    {
      "name": "Big Corpo",
      "num_of_emp": 10000,
      "ceo": "Mary",
      "rating": 3.6
    },
  {
    "name": "Small Startup",
    "num_of_emp": 3,
    "ceo": null,
    "rating": 4.3
  }
]`;

console.log(JSON.parse(companies));
```

`console.log(JSON.parse(companies)[1].name);` -> `"Small Startup"`




















