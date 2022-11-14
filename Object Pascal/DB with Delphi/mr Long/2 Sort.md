[[_ 0 DB (local .mdb) in Delphi]]


# Sort DB
https://www.youtube.com/watch?v=kV2g0yKeB7s&list=PLxAS51iVMjv_buZ6zbd6k3cMWrTrU0Nio&index=2

```pascal
procedure TForm5.Button1Click(Sender: TObject);
begin
dmDB.tblAnimal.Sort := 'Category ASC, Breed DESC' ;

end;
