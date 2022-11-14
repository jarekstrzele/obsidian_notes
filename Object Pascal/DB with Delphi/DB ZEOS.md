

# How to install
https://www.youtube.com/watch?v=YH2as9rij7o

To use:
- create new VCL Project
- palette -> Zeos Access
	- TZConnection
	- TZQuery
	- DBGrid
	- DataScource
now
- `DataSource` - its property `DataSet`: `ZQuery1` (this is a name of `TZQuery` component) 
- DBGrid - its property `DataSource` : `DataSource 1` (this is a name of `DataScource` component)
- and connect ZQuery to ZConnection by Zquery property `Connection` : `Connnection1`(this is a name of TZConnection component)
- and now:
	-  connect ZConnection to DB, set property `HostName` : to  `localhost` and
	-  property `Database` to `name of your MySQL database` and
	-  choose the `Protocol` propety and set is to `mysql` and
	- `User` : `root`
	- `Password` : `,,e,w,`
	- `LibraryLocation` : `libmysql.dll`
`Connected` : `true`


-------------
# ZEOS and SQLite
#delphi/zeos #sqlite  #youtube

https://www.youtube.com/watch?v=C8Oxq-jJ2ZY

1. you need `sqlute3.dll` from www.sqlite.irg
2. this file save with your project (?)
3. connect your project with this file `ZConn.LibraryLocation:=ExtractFilePath(Application.ExeName)+'sqlite3.dll'


New project
- From Zeos
	- ZConnection (Name `ZConn`)
	- TZQuery x2
	- DataSource (from data access)
	- TDBGrid (connect to `ZConn`)

Button Open Data Base
```pascal

procedure TForm6.Button1Click(Sender: TObject);
begin
 ZConn.Protocol := 'sqlite-3' ;
 ZConn.LibraryLocation:=ExtractFilePath(Application.exeName)+'sqlite3.dll' ;
 if not FileExists(ZConn.LibraryLocation) then  Exit ;
 ZConn.Database:=ExtractFilePath(Application.ExeName) + 'testdb.s3db' ;
 if not FileExists(ZConn.Database) then  Exit ;
 ZConn.Connect;
 Label2.Caption:='testdb.s3db' ;
 ComboBox1.Items.Clear ;
 ZConn.GetTableNames('', ComboBox1.Items) ;
 ComboBox1.ItemIndex:=0 ;
 ComboBox1.OnChange(Self) ;
end;
```

Button Create Table
```pascal
procedure TForm6.Button2Click(Sender: TObject);
begin
	ZQuery1.Close;
	ZQuery1.SQL.Clear;
	ZQuery1.SQL.Add('CREATE TABLE if not exists testtbl1(id INTEGER PRIMARY KEY AUTOINCREMENT NOT NULL,'+'name VARCHAR(255), surname VARCHAR(255), UNIQUE(id))') ;
	ZQuery1.ExecSQL ;
	ComboBox1.Items.Clear ;
	ZConn.GetTableNames('', ComboBox1.Items) ;
	ComboBox1.ItemIndex:=0 ;
	ComboBox1.OnChange(Self) ;
end;
```

COMOBOX
```pascal
procedure TForm6.ComboBox1Change(Sender: TObject);
var i : integer ;
begin
ZQuery2.Close;
ZQuery2.SQL.Add('Select * from ' + ComboBox1.Text) ;
ZQuery2.Open;

for i:= 0 to DBGrid1.Columns.Count-1 do
begin
	DBGrid1.Columns[i].Width:=100;
end;

end;


```

INSERT
```pascal
procedure TForm6.Button3Click(Sender: TObject);
begin
if Edit1.Text<>'' then
	begin
		ZQuery1.SQL.Clear;
		ZQuery1.SQL.Add('Insert into testtbl(name, surname) values (' + QuotedStr(Edit1.Text)+','+QuotedStr(Edit2.Text)+')');
		ZQuery1.ExecSQL;
		Combobox1.OnChange(self);
	end;
end;
```

UPDATE
```pascal
procedure TForm6.Button4Click(Sender: TObject);
begin
  ZQuery1.SQL.Clear;
  ZQuery1.SQL.Add('Update testtbl set name='+QuotedStr(Edit3.Text)+',surname='+QuotedStr(Edit4.Text)+' where id='+QuotedStr(Label8.Caption)) ;
  Zquery1.ExecSQL;
  Combobox1.OnChange(self);
end;

```
DELETE
```pascal
procedure TForm6.Button5Click(Sender: TObject);
begin
ZQuery2.Delete ;
end;
```

Grid > Events > OnCellClick > (Write) `DBGrid1CellClick` -> procedure
```pascal
procedure TForm6.DBGrid1CellClick(Column: TColumn);
begin
Edit3.Text := ZQuery2.FieldByName('name').AsString;
Edit4.Text:=Zquery2.FieldByName('surname').AsString;
Label8.Caption:=ZQuery2.FieldByName('id').AsString;
end;
```




------------

# MYSQL with ZEOS
https://www.youtube.com/watch?v=_WFMYFz68RQ

server: https://www.usbwebserver.net/webserver/
root
usbw

You need `libmysql.dll` in the same folder where `.exe` file will be

in group component:
	- pola tEdit: host, port, user, password
	- buttons: connect, disconnect
status bar

`TZConnect`, `TZQuery`, 

configure the connection button
```pascal
procedure TForm6.Button1Click(Sender: TObject);
var i : integer ;

begin
with ZConnection1 do 
	begin
		Diconnect;
		Protocol:='mysql' ;
		LibraryLocation:=ExtractFilePath(Application.ExeName)+'libmysql.dll' ;
		HostName:=txtHost.Text;
		Port:=StrToInt(txtPort.Text) ;
		User:=txtUser.Text;
		Password:=txtPass.Text;
		Connect;
	end;


  cboDatabases.Items.Clear ; //combobox 
  ZConnection1.GetCatalogNames(cboDatabases.Items) ;
  cboDatabases.ItemIndex:=0 ;

end;

```

a new group box component: Database and tables

disconnect button
```pascal
procedure TForm6.Button2Click(Sender: TObject);
begin
ZConnection1.Disconnect ;
end;
```
Config `ZConnection1`
Event `AfterConnect`: `ZConnectionAfterConnect`
Event `AfterDisconnect`: `ZConnectionAfterDisconnet`

```pascal
procedure TForm6.ZConnectionAfterConnect(Sender: TObject);
begin
StatusBar1.Panels[0].text:='Connected';
end;

procedure TForm6.ZConnectionAfterDicconnect(Sender: TObject);
begin
StatusBar1.Panels[0].text:='Disconnected';
end;

```




































