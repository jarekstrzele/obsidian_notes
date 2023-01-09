[[_ 0 DB (local .mdb) in Delphi]]


# First connect
Delph > File > New > data module (save in the same folder as the main project) change name
Each forms of your project will be connected to this data module.


In Tool Palette find `ADOConnection` this komponent will directly connect to DB:
- change name into `conCDDatabase`
- Property `ConnectionString`  in that property you set the settings of connection
	- provider Jet
	- connection CD_database.mdb
	- `LoginPrompt` : false
- in Tool Palette find tADOTable 
	- find property "connection" and set connection to the `conCDDatabase`
	- property TableName -> CdTable (czerpie dane z okiku .mdb)
	- `Active` : true

To see your interaction with dabase:
- tool paletteL `TDataSource` and connect it to table (each table will have its TDataSource)
	- name it dscCD
	- property DataSet set to your table (a new name: dscCD)
- in your `Unit` add `TDBGrid` to see data in the table  + `TDBNavigator` (TDB .... a lot of)
- you have to connect TDBGrid with TDataScource, but first you have to connect `Unit` with `Data module`

```pascal
//...
uses
	//....
	, dmCD_u // now you have an access that every thing is in data module
```
and now in the ptoperty `DataScource` of TDBGrid component you have access to `dmCD.dscCD`
on the TDBGrid righ mouse click -> column Editor

connect Navigator to TDataSource from  DataModule
Add `TDBEdit` component, connect it with DataSource and find its property `DataField` to check which column value will be show
