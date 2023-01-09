[[_ 0 DB (local .mdb) in Delphi]]


# Extracting Data From a DataBase

https://www.youtube.com/watch?v=yD-PfGmToRo&list=PLxAS51iVMjv_buZ6zbd6k3cMWrTrU0Nio&index=3

## ADOTable methods

method | Description
---| ---
First (Last) | Moves pointer to first record; Example: `tblCD.first;`
Next (Prior) | Moves pointer to next record; Example: `tblCD.Next ;`
EOF | Returns TRUE if pointer is at the and of the database table <br > and FALSE if it is not. <br > Example: `if tblCD.EOF then`
RecordCount | Return the number of records in the table as in integer <br> example: `iNum := tblCd.RecordCount ;`

### Going through all records in a database in Delphi
Use the ADO TABLE (e.g. `tblCD`)
1. `tblCD.FIrst`
2. Loop till end of table: `whole NOT tblCD.eof do`
3. In loop move to next record: `tblCD.Next`

traversing a DB | tranversing a text file
--- | ---
`tlbCD.FIrst ;` | `Reset(myFile) ;`
`while NOT tblCD.EOF do begin   tblCD.Next end ;` | `while NOT EOF(myFIle) do begin  ReadLn(myFile, sLine) ;   end ;`

### to access data
`tableName['NameOfField']`
`sArt := tblCd['Artist'] ;`
remember about DATA TYPE
`iNum:=tblCD['SomeIntData']`

```pascal

procedure TForm5.Button1Click(Sender: TObject);
var
  rSum, rAve : real ;
 
begin
rSum := 0 ;

with dmDB do
  begin
    tblAnimal.First ;
    while NOT tblAnimal.eof do
    begin
      rSum := rSum + tblAnimal['ListPrice'] ;

      tblAnimal.Next ;
    end;

    rAve := rSum / tblAnimal.RecordCount ;
    showmessage('Average is ' + FloatToStrf(rAve, ffFixed, 8, 2)) ;
  end ;


end;

```

```pascal
procedure TForm5.Button1Click(Sender: TObject);
var
  rSum, rAve : real ;
  iCount : integer ;
  sBreed : string ;
begin
rSum := 0 ;
iCount := 0 ;
sBreed := edtInput.Text ;

with dmDB do
  begin
    tblAnimal.First ;
    while NOT tblAnimal.eof do
    begin
      if tblAnimal['Breed'] = sBreed then
        begin
          rSum := rSum + tblAnimal['ListPrice'] ;
          inc(iCount) ;
        end ;
      tblAnimal.Next ;
    end;

    rAve := rSum / iCount ;
    showmessage('Average is ' + FloatToStrf(rAve, ffFixed, 8, 2)) ;
  end ;


end;

```
