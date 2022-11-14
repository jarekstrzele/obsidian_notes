https://www.youtube.com/watch?v=O03E6aKC8IE

#sqlite  #delphie #youtube 

# Delphi and SQLite
- in SQLite Studio create a db and a table
- in Delphi create new projcet, Data Explorer > FireDac > SQLIte database > right click and add new connection (name, choose a SQLite DB) and drug and drop this connection on the Form
- Property` Connected` : change for true
- drag and drop your table from Data Explorer > SQLiteTutorial
- right click on this table icon > Fields Editor > right click on this fileds 'Add all fields'
- select all fileds without id and drop it on the form
- select TDBNavigator and assigne a DataSource
- ==double click on the form== `<tablename>.Open ;`
> If the db is locked :
> 	- Click on connection icon, find `Params` property, inside that `LockingMode` set on `ImNormal` and `SharedCache` on `False`
> 	- or right lick on this icon and select Connection Editor
	







