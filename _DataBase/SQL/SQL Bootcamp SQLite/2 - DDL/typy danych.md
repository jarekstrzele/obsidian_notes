[[_ DDL SQLite]]


# Typy danych
SQLite jest dynamiczny
`SELECT TYPEOF(20);`
`SELECT TYPEOF(20.3);`
`SELECT TYPEOF("20");`
`SELECT TYPEOF(true);`
`SELECT TYPEOF(null);`
`SELECT TYPEOF(x'0101');` blob




PIĘĆ KLAS:
1. `NULL`
2. `INTEGER` liczba całkowita ze znakiem
3. `REAL` liczba zmiennoprzecinkowa
4. `TEXT` ciąg znaków (zmienna długość)
5. `BLOB` Binary Large Object (zdjęcia, muzyka, video, pdf) (zmienna długość)

brak
- boolean -> zamiast `1 0`
- data i czas -> zamiast 
	- TEXT (YYYY-MM-DD HH:MM:SS.SSS) 
	- INTEGER (czas uniksowy 1970 00:00:00)
	- REAL (juliańska)
- 




