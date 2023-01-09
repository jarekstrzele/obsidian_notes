[[_  0 Full Beginner Crash Course]]

New `data module`. (name: `dmConnection_u` , you have to add that to your unit Form) 
```pascal
uses
  Winapi.Windows, Winapi.Messages, System.SysUtils, System.Variants, System.Classes, Vcl.Graphics,
  Vcl.Controls, Vcl.Forms, Vcl.Dialogs, dmConnection_u;

```

1. `TADOConnection` (it connects to the database )
	1. ConnectionString (properties) -> build
	2. LoginPrompt (properties) -> false
2. `TADOTable1`
	1. tablename
	2. connection
3. `DataSource`
	1. Name `dsPets`
	2. Dataset to point $2.$
	3. 

In the form `DBGrid`
- `datasourc` to 
- TADOTable > property `Active` : True


## DBNavigator
`DataScource` : 

## INSERTING DATA to DB

Add a button
1. get all data (columns in table) from a user
use inputboxes, check if the `tbl...` has the property `ReadOnly:False` 
```pascal

implementation

{$R *.dfm}

procedure TForm6.btnAddClick(Sender: TObject);
var
  sCategory, sBreed: string    ;

begin
  sCategory:= Inputbox('Category', 'Write the category', 'bird') ;
  sBreed:= Inputbox('Breed', 'Write the breed', 'Parrot') ;

  with dmConnection do
  begin
    tblBreed.Insert ;
    tblBreed['Category'] := sCategory ;
    tblBreed['Breed']:=sBreed;

    tblBreed.Post ; // to save changes in the DB
  end;


end;

```

## EDITING THE DATA in a database
a new button to edit

```pascal
procedure TForm6.btnEditClick(Sender: TObject);
var
  sCategory, sBreed, sNewBreed: string ;

begin
 sCategory := inputBox('Category', 'Cat to change', 'Bird') ;
 sBreed := inputBox('Breed', 'Bred to change', 'Canary') ;
 sNewBreed := InputBox('New Breed', 'New Breed', 'new canary') ;

 with dmConnection do
 begin
   if (tblBreed.Locate('Category', sCategory, []) and
       tblBreed.Locate('Breed', sBreed, [])) then
   begin
     tblBreed.Edit ;
     tblBreed['Breed'] := sNewBreed ;
     tblBreed.Post ;
   end else
   begin
     ShowMessage('Not found') ;
   end;
 end;
end;

```

## Deleting the data in a database
```pascal
procedure TForm6.btnDeleteClick(Sender: TObject);
var
  sCategory, sBreed : string ;
begin
  sCategory := inputBox('Category', 'Cat to change', 'Bird') ;
  sBreed := inputBox('Breed', 'Bred to change', 'new canary') ;

   with dmConnection do
 begin
   if (tblBreed.Locate('Category', sCategory, []) and
       tblBreed.Locate('Breed', sBreed, [])) then
   begin
     tblBreed.Delete;
     ShowMessage('Record deleted') ;
   end else
   begin
     ShowMessage('Not found') ;
   end;

 end;
```

## Filtering a database
in `TADOTable` Filtered : True, and property Filter
```pascal
procedure TForm6.btnFilterClick(Sender: TObject);
begin
with dmConnection do
  begin
    tblPets.Filtered := True ;
    tblPets.Filter := 'Breed = ''Shark'' ' ; //'AnimalID < 10' ;
  end;
end;

```

`  tblPets.Filter := '(AnimalID <5) or (AnimalID > 20)' ;`

`tblPets.Filter := '(AnimalID <5) and (Category = ''Fish'') ' ;`

## Calculations with database
```pascal
procedure TForm6.btnCalcClick(Sender: TObject);
var
  iCount: integer ;
  iTotal : real ;

begin
 iTotal := 0 ;
 iCount := 0 ;

with dmConnection do
   begin
     tblPets.Open ;
     tblPets.First ; // curson on the first position

     while not tblPets.Eof do
      begin
        //iTotal := iTotal + tblPets['ListPrice'] ;
        iTotal := iTotal + tblPets.FieldByName('ListPrice').AsFloat ;
        Inc(iCount) ;
        tblPets.Next ;
      end;

   end;
 ShowMessage(IntToStr(iCount) + ' number of rows and total listprice: '
 + FloatToStr(iTotal) ) ;

end;
```


## Sorting
```pascal
procedure TForm6.btnSortClick(Sender: TObject);
begin
with dmConnection do
 begin
   tblPets.Sort := 'Name ASC' ;
 end;
end;
```

`DESC`

```pascal
procedure TForm6.btnSortClick(Sender: TObject);
begin
with dmConnection do
 begin
   tblPets.Sort := 'Name ASC, Category DESC ' ;
 end;
end;

```



## Searching
```pascal
procedure TForm6.btnSearchClick(Sender: TObject);
begin
with dmConnection do
  begin
    if tblPets.Locate('Name', 'Tina', []) then
    begin
      ShowMessage('Tina found on ' + IntToStr(tblPets['AnimalID']) ) ;
    end;

  end;
end;
```


`  if tblPets.Locate('Name', 'Tina', [loCaseInsensitive]) then ...`

```pascal
with dmConnection do
  begin
    if tblPets.Locate('Name', 'Ti', [loCaseInsensitive, loPartialKey]) then
```

## Working with multiple forms
File> NEw> VLC - Form - Delphi

change the name
`frmManipulate_u` 
move butns to the new form (you have to cut and paste code of the btns)
in the new form you have to import `dmConnection`

in the main form you have to import the ew form
`use ..  frmManipulate_u;`

in the main from you have a button 'Manipulate DB'
```pascal
procedure TForm6.btnManipulateDBClick(Sender: TObject);
begin
   frmManipulateDB.Show ;
end;
```


to hide 
```pascal
procedure TForm6.btnManipulateDBClick(Sender: TObject);
begin
   frmManipulateDB.Show ;
   Self.Hide ;
end;
```
It hides a main form that will be working on the background (Task manager > User  , to stop)


to close a form
`Self.Close`


From the form `Manipulation` you can make import from main form but you can:
`Application.MainForm.Show ;` It is a cross refrence





