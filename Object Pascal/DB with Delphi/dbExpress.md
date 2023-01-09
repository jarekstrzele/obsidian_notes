https://4programmers.net/Delphi/Kompendium/Rozdzia%C5%82_17

# dbExpress
OGÓLNY SCHEMAT
1. Make a connection 
	1. `SQLConnection`
		1. driver to the data base 
2. Define interaction (Table/Query) - to hold your result set 
3. Provide a provider - to provide data to some  holder of that result set (to TClientDataSet)
4. Define a TClientDataSet
5. Connect to the DataScource (to take the information and forward to some data controls and allow to work with data) (--> Data Controls: Navigators, Edits, Images)
	1. display data
	2. navigate of data
	3. edite of data



Podstawą korzystania z różnych baz  są ==sterowniki==
(umożliwiają dotęp do systemów baz i pełnia rolę pośredników)

Do łączenia z serwerem MySQL używamy `TSQLConnetion` (potrzebna jest biblioteka `libmysql.dll`)
`ConnectionName`: `MySQLConnection`

