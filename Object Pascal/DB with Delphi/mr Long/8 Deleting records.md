[[_ 0 DB (local .mdb) in Delphi]]



# Deleting records
- Use the ADO Table
- Use the `Delete` function
	- Deletes the record where the pointer is currentrly
	- Pointer will move to the next record after the delete process

- Deleting **ONE** record
	- use `Locate` to move the pointer to the record you want to delete
- Deleting multiple records
	- Use the traverse algorithm to delete multiple records

Delete **ONE** record
```pascal
procedure TForm5.btnDeleteClick(Sender: TObject);
var
  iCityId : integer ;
  sCity : string ;
begin
  iCityId := StrToInt(InputBox('City Id', 'City Id tha must be deleted', '20347')) ;

with DataModule1 do
begin
  if tblCity.Locate('CityID', iCityId, []) = true then
    begin
      tblCity.Delete ;
      showmessage('Record deleted!') ;
    end
  else
    begin
       showMessage('I did not find the record') ;
    end;


end;
```


Delete **MANY** records
```pascal
procedure TForm5.btnDeleteClick(Sender: TObject);
var
  sState: string ;
begin
   sState    := InputBox('State', 'State that must be deleted', 'AK') ;

   with DataModule1 do
    begin
       while NOT tblCity.EOF do
        begin
          if tblCity['State'] = sState then
             tblCity.Delete // automatically goes to the next
          else
             tblCity.Next ;
        end;

    end;


end;
```









