[[_ 0 DB (local .mdb) in Delphi]]



# Adding a new record

- use the ADO Table
- put the database into INSERT mode
- add all the valuies you have to the necessary fields
- POST the results to the database


```pascal
procedure TForm5.btnInsertClick(Sender: TObject);
var

  sZipCode, sState, sCity : string ;
begin
   sCity := 'Olsztyn' ;
   sZipCode := '999' ;
   sState := 'SS' ;

   DataModule1.tblCity.Insert ;
   DataModule1.tblCity['City'] := sCity ;
   DataModule1.tblCity['ZipCode'] := sZipCode ;
   DataModule1.tblCity['State'] := sState ;

   DataModule1.tblCity.Post ;

end;
```

## Ensuring a unique primary key
- make sure the primary key field is an **Autonumber**
- if primary key is a number
	- find the largest primary key by **sorting** the primary key field
	- use that value + 1 as your new primary key
- Generate code
	- use **locate** to first check if that code exists

```pascal

procedure TForm5.btnInsertClick(Sender: TObject);
var

  sZipCode, sState, sCity : string ;
begin
   sCity := 'Olsztyn' ;
   sZipCode := '999' ;
   sState := 'SS' ;

   DataModule1.tblCity.Insert ;
   DataModule1.tblCity['City'] := sCity ;
   DataModule1.tblCity['ZipCode'] := sZipCode ;
   DataModule1.tblCity['State'] := sState ;

   DataModule1.tblCity.Post ;

end;
```

#### checking CityId
```pascal
procedure TForm5.btnInsertClick(Sender: TObject);
var
  iCityId := integer ;
  sZipCode, sState, sCity : string ;
begin
   iCityId := 33123 ;
   sCity := 'Olsztyn' ;
   sZipCode := '999' ;
   sState := 'SS' ;
   
   if DataModule1.tblCity.Locate('CityId', iCityId, []) = true then
	   begin
		   showMessage('Not a unique primery key') ;
		end
   else
	   begin
	      DataModule1.tblCity.Insert ;
	      DataModule1.tblCity['CityID'] := iCityid ;
	      DataModule1.tblCity['City'] := sCity ;
	      DataModule1.tblCity['ZipCode'] := sZipCode ;
	      DataModule1.tblCity['State'] := sState ;
		  DataModule1.tblCity.Post ;
		end ;

end;
```

#### Calculating CityId
```pascal
procedure TForm5.btnInsertClick(Sender: TObject);
var
  iCityId := integer ;
  sZipCode, sState, sCity : string ;
begin
	sCity := 'Olsztyn' ;
	sZipCode := '999' ;
	sState := 'SS' ;

	DataModule1.tblCity.Sort := 'CityID ASC';
	DataModule1.tblCity.Last ;
	iCityId = DataModule1.tblCity['CityID'] + 1 ;

    begin
	   DataModule1.tblCity.Insert ;
	   DataModule1.tblCity['CityID'] := iCityid ;
	   DataModule1.tblCity['City'] := sCity ;
	   DataModule1.tblCity['ZipCode'] := sZipCode ;
	   DataModule1.tblCity['State'] := sState ;
	   DataModule1.tblCity.Post ;
	end ;

end;
```












