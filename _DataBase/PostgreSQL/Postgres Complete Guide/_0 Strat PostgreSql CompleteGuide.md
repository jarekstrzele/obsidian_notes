#databases  #postgres  #udemy  #grider_stephen

# pg-sql.com

[[2 Filtering Records]]
[[3 Working with Tables]]







---
# Start Postrgres

![[client-postgres.excalidraw]]


How to store  a list of  large cities  in a database?
https://en.wikipedia.org/wiki/List_of_largest_cities

## Database Design Process
1. What kind of *thing* are we storing?
	We are storing a list of cities
	`We should to make table *cities*`
2. What properties does this thing have?
	Each city has a name, country, population and area
	`We should make columns`
3. What *type* of data does each of those properties contain?
	name -> string, 
	country->string, 
	population->number, 
	area->number
	`Each column should indicate the type of data that it is going to store`

Tokyo, Japan, 37400068, 8223
Delhi, India, 28514000, 2240
Shanghai, China, 255280000, 4015

### `pg-sql.com`

### create a table
```sql
CREATE TABLE cities(
  name VARCHAR(50),
  country VARCHAR(50),
  population INTEGER,
  area INTEGER
  
  );
```
### Insert data
```sql
INSERT INTO cities(name, country, population, area)
VALUES('Tokyo', 'Japan', 38505000, 8223) ;
```
```sql
INSERT INTO cities(name, country, population, area)
VALUES 
	('Delhi', 'India', 28125000, 2240) ,
	('Shanghai', 'China', 22125000, 4015) ,
	('Sao Paulo', 'Brazil', 20935000, 3043)  ;
```

### Retrieve data from DB
```sql
SELECT * FROm Cities;

SELECT name, population/area as population_density FROm Cities;
```

## String operators and Functions
`||` or `CONCAT()` - join two string
`LOWER()` - gives a lower case string
`LENGTH()` - gives number of characters in a string
`UPPER()` - gives an upper case string

`SELECT name || ', ' || country FROm Cities;`
```sql
Tokyo, Japan
Delhi, India
Shanghai, China
Sao Paulo, Brazil
```

```sql
SELECT CONCAT(name, ', ', country) FROM Cities;
Tokyo, Japan
Delhi, India
Shanghai, China
Sao Paulo, Brazil
```

















