[[_ SQLite]]
[[_ Groupowanie danych SQLite]]

---

## Funkcje agregujące

### count
ilość nie pustych wierszy
`select count(*) as TotalRows FROM Product;`

`select count(SupplierId) From Product;`
`select count(DISTINCT SupplierId) as NumOfSuppliers From Product;`

> count nie liczy wierszy z NULL


### sum
`select SUM(UnitPrice) as TotalSum From Product;`

### avg
`select AVG(UnitPrice) as TotalSum From Product;`
`select AVG(DISTINCT UnitPrice) as TotalSum From Product;`

### MIN,   MAX



