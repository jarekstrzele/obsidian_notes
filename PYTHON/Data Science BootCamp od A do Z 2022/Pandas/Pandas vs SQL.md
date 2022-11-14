[[0-Pandas wprowadzenie]]
[[2-Case Study Google App Store]]

___

# Pandas vs SQL

## Przygotowanie
```py
import pandas as pd
import numpy as np

url = ('https://storage.googleapis.com/esmartdata-courses-files/ds-bootcamp/online_retail.xlsx')

retail_raw = pd.read_excel(url)

retail_raw.head()

# surowe dane pozostawiamy nie zmieniane
retail = retail_raw.copy()

# sprawdzamy, jakie typy danych są w kolumanch
retail.info()

# sprawdzamy, jakie są statystyki
retail.describe()

# sprawdzamy, czy są braki w danych
retail.isnull().sum()

```

Porządkujemy dane
```py
# usuwamy braki
retail = retail.isnull().sum()
retail = retail.dropna()

#python/maska_logiczna 
# retail.Quantity >= 0 # chcemy tylko wartości dodatnie
retail = retail[retail.Quantity >= 0]

# CustomerID z typu float na str
#python/apply
retail.CustomerID = retail.CustomerID.apply(lambda x: str(int(x)))


```

## Porównanie
DataFrame jest jak tabla.
```py

# SELECT * FROM retail;
retail

# SELECT Quantity, UnitPrice, CustomerID from retail;
retail[['Quantity', 'UnitPrice', 'CustomerID']]

# SELECT Quantity, UnitPrice, CustomerID from retail LIMIT 10;
retail[['Quantity', 'UnitPrice', 'CustomerID']].head(10)
retail[['Quantity', 'UnitPrice', 'CustomerID']][:10]

# SELECT * FROM retail WHERE CustomerID='17850';
#python/maska_logiczna 
retail.CustomerID == '17850'
retail[retail.CustomerID == '17850']
# z query
#python/pandas_query
retail.query('CustomerID == "17850"')

# SELECT * FROM retail WHERE CustomerID='17850' AND UnitPrice>5;
retail[(retail.CustomerID == '17850') & (retail.UnitPrice>5)]

# SELECT * FROM retail WHERE CustomerID='17850' OR Country='France';
retail[(retail.CustomerID == '17850') | (retail.Country == 'France')]

# SELECT * FROM retail WHERE InvoiceNo is null;
#python/maska_logiczna 
retail.InvoiceNo.notnull() #-> maska logiczna
retail[retail.InvoiceNo.notnull()]
# retail[retail.InvoiceNo.isnull()]

```

GROUP BY
```py
# SELECT CustomerID, count(*) FROM retial GROUP BY CustomerID;
retail.groupby('CustomerID').size()

CustomerID 
12346 1 
12347 182 
12348 31 
12349 73 
12350 17 
...

# SELECT CustomerID, avg(Revenue), count(*) FROM retial GROUP BY CustomerID
# średnia wartość transakcji klient
# najpierw tworzymy nową kolumnę
retail['Revenue'] = retail.Quantity * retail.UnitPrice
retail.groupby("CustomerID").aggregate({'Revenue': np.mean, 'CustomerID':np.size})

# jeszcze możamy kolumnom nadać nowe nazwy
retail.groupby("CustomerID").aggregate({'Revenue': np.mean, 'CustomerID':np.size}).\
rename(columns={'Revenue': "RevenueAverage", 'CustomerID': 'CustomerIDCOunt'})



# SELECT InvoiceDateDay, sum(Revenue) FROM retail GROUP BY InvoiceDateDay;
#najpierw tworzymy nową kolumnę; 'dt' pozwala nam dostać się do dnia w dacie
retail['InvoiceDateDay'] = retail.InvoiceDate.dt.day

retail.groupby('InvoiceDateDay').aggregate({'Revenue':np.sum})



```

ORDER BY
```py
# SELECT * FROM retail ORDER BY Quantity DESC LIMIT 5;
retail.nlargest(n=5, columns='Quantity')


# SELECT * FROM retail ORDER BY Quantity LIMIT 5;
retail.nsmallest(n=5, columns='Quantity')

```












