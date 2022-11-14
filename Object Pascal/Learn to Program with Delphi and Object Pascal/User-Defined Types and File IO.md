[[_ 0 intro Delphi Object Pascal]]


# User-Defined Types

```pascal
unit Utunit;

interface

uses
  SysUtils, WinTypes, WinProcs, Messages, Classes, Graphics, Controls,
  Forms, Dialogs, StdCtrls;

type
  // My type definitions
  Str10 = string[10];
  Str5  = string[5];
  DaysInWeek = (Mon,Tue,Wed,Thu,Fri,Sat,Sun);
  UpperCase = 'A'..'Z';

  // Form definition
  TForm1 = class(TForm)
    Button1: TButton;
    Button2: TButton;
    Button3: TButton;
    Memo1: TMemo;
    procedure Button1Click(Sender: TObject);
    procedure Button2Click(Sender: TObject);
    procedure Button3Click(Sender: TObject);
  private
    { Private declarations }
  public
    { Public declarations }
    function DayStr( day : DaysInWeek ) : string;
  end;


var
  Form1: TForm1;

implementation

{$R *.DFM}

function TForm1.DayStr( day : DaysInWeek ) : string;
begin
   case( day ) of
     Mon : result := 'Monday';
     Tue : result := 'Tuesday';
     Wed : result := 'Wednesday';
     Thu : result := 'Thursday';
     Fri : result := 'Friday';
     Sat : result := 'Saturday';
     Sun : result := 'Sunday';
     else result := 'Unknown';
   end;
end;

{
// Here the function above has been rewritten to avoid multiple 'return'
// points...
function TForm1.DayStr( day : DaysInWeek ) : string;
var
   strDay:string;
begin
   case( day ) of
     Mon : strDay := 'Monday';
     Tue : strDay := 'Tuesday';
     Wed : strDay := 'Wednesday';
     Thu : strDay := 'Thursday';
     Fri : strDay := 'Friday';
     Sat : strDay := 'Saturday';
     Sun : strDay := 'Sunday';
     else strDay := 'Unknown';
   end;
   result := strDay;
end;
}

procedure TForm1.Button1Click(Sender: TObject);
const
  GREETING = 'Hello world';
var
  s10     : Str10;
  s5      : Str5;
  today   : DaysInWeek;
  letter  : UpperCase;
begin
  s10 := GREETING;
  s5 := GREETING;
  today := Wed;
  letter := 'X';
  ShowMessage( Format( 's10 = %s, s5 = %s, today= %s, letter = %s',
                       [s10,s5,DayStr(today),letter] ));
end;

procedure TForm1.Button2Click(Sender: TObject);
var
   i : integer;
   s : string;
begin
   s := '';
   for i := 0 to 6 do
       s := s + DayStr( DaysInWeek ( i ) ) + ' ';
   ShowMessage( 'Days of week are: ' + s );
end;

procedure TForm1.Button3Click(Sender: TObject);
type
   CD = string[45];
var
   cdChanger : array[1..10] of CD;
   i : integer;
begin
  cdChanger[1] := 'Dolly Parton''s Great Hits';
  cdChanger[2] := 'Village People Sing Led Zeppelin';
  cdChanger[3] := 'The Wombles House-Mix';
  cdChanger[4] := 'Wagner''s Quiet Bits';
  cdChanger[5] := 'Pavarotti Sings ABBA';
  cdChanger[6] := 'George Michael In Neasden';
  cdChanger[7] := 'Judas Priest Great Love Songs';
  cdChanger[8] := 'The Andrews Sisters Lost Sessions';
  cdChanger[9] := 'Ken Dodd Sings Buddy Can You Spare A Buttie?';
  cdChanger[10] := 'Max Bygraves Tribute To MeatLoaf';
  for i := 1 to 10 do
      Memo1.Lines.Add(cdChanger[i]);
end;

end.
```

---
# Records type
```pascal
type
	<TypeIdentifier> = record
		<FieldIdentifier> : <Type> ;
		< [Optionally more fields] >
	end ;
```

example:
```pascal
type
  Str30 = string[30] ;

  CD = record
    name : Str30 ;
    artist : Str30;
    price : double ;
    CDlabel : str30 ;
  end;
```

One CD and an array of CDs:
```pascal
var
	aCD : CD;
	myCDs : array[1..4] of CD ;
```
Initialize:
```pascal
aCD.name := 'Loads of Nice' ;
aCD.artist : 'Blaise & The PAscalettes' ;
aCD.price := 0.75 ;
aCD.CDlabel := 'Seedy CDs';

myCDs[1].name := 'Great Hits' ;
myCDs[1].artist := 'Dolly Parton' ;
myCDs[1].price := 10.75 ;
myCDs[1].CDlabel:= 'Great Records' ;
```
## File IO
```pascal
uses ....
type
	Str30 = string[30] ;

	CD = record
		name : Str30 ;
		artist : Str39 ;
		price : double ;
		cdlabel : Str30 ;
```

`AssignFile( <File variable>, <File Name>) ;`
`Reset(<File variable> ) ;`
`Seek(<File variable>, <Position in File> ) ;`
`Write( <File variable>, <Record> ) ;`
`CloseFile( <File variable> )l`















