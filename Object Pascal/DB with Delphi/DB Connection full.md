#youtube #delphi #databases 
https://www.youtube.com/watch?v=X5TZH2SrIlU



# DB Connection
File > new > Windows VCL

Palette > TPanel ( x 4)
	- caption: Database Connector

- add .mdb to the projet folder
- TADOConnection
	- ConnectionString , choose a db file
	- uncheck loginPrompt propetry
- ADOTable
	- to connect this component to TADOConnection set `Connection` property  
	- `TableName` choose the table name from the db
- TDataSource and set `DataSet` : Table name from ADOTable component
- TDBNavigator and
	-  set `DataSource` : DataSourse component
	- set `Kind` : dbnVertical
- TDEdit, TLabel
- TDBGrid connect -> property `DataSource`: compomentDataSource1
- TDBTable `activate` : True
- DBEdit  set `DataSource`, and `DataField`



