[[_ 0 DB (local .mdb) in Delphi]]

# Editing a current record

- use the ADO TABLE
- put the database into EDIT mode
- Add all the values you have to the necessary fields
- POST the results to the database

- editing ONE Record
	- use `Locate` to move the pointer to the record you want to change
- editing MUTIPLE records
	- use the travers algorithm to change multiple records

ONE RECORD
```pascal
procedure TForm5.btnEditClick(Sender: TObject);
var iAreaCode, iCityID : integer ;

begin
  iCityID := StrToInt( InputBox('CityID',
                          'City ID of the record you want to change', '10') ) ;

  iAreaCode := StrToInt( InputBox('Value',
                                  'Change AreaCode value by: ', '20' ) ) ;

with DataModule1 do
begin
  if tblCity.Locate('CityID', iCityID, []) = true then
  begin
     tblCity.Edit ;
     tblCity['AreaCode'] := iAreaCode ;
     tblCity.Post ;
  end
  else
    begin
      showMessage('Record not found!') ;
    end;

end;
```

Many RECORDS
```pascal

procedure TForm5.btnEditClick(Sender: TObject);
var
  iAreaCode, iCityID : integer ;
  sState : string ;


begin
  sState := InputBox('State', 'State you want to change', 'OK')  ;

  iAreaCode := StrToInt( InputBox('Value',
                                  'Change AreaCode value by: ', '88' ) ) ;

with DataModule1 do
begin
tblCity.First ;
while NOT tblCity.EOF do
  begin
     if tblCity['State'] = sState then
      begin
        tblCity.Edit ;
        tblCity['AreaCode'] := iAreaCode ;
        tblCity.Post ;
      end;


    tblCity.Next
  end;
```


