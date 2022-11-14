#udemy #object_pascal #delphi 
#collingbourne_huw

[[Fundamental of Pascal]]
[[Procedures and Functions]]
[[Data Types, Operators, Scope]]
[[User-Defined Types and File IO]]



---
# Intro Delphi and Object Pascal

commercial: Delphi
free: Lazarus

## First app Hello
Lazarus
- new project Application
- *Tedit* 

AgeTest - example
```pascal
unit Age1;

{$mode objfpc}{$H+}

interface

uses
  SysUtils, Messages, Classes, Graphics, Controls,
  Forms, Dialogs, StdCtrls;

type
  TForm1 = class(TForm)
    Button1: TButton;
    ScrollBar1: TScrollBar;
    Label1: TLabel;
    AgeLabel: TLabel;
    Label2: TLabel;
    Label3: TLabel;
    procedure Button1Click(Sender: TObject);
    procedure ScrollBar1Change(Sender: TObject);
  private
    { Private declarations }
  public
    { Public declarations }
  end;

var
  Form1: TForm1;

implementation

{$R *.lfm}

procedure TForm1.Button1Click(Sender: TObject);
{========= START OF TUTORIAL CODE ========}
{ Declare variables }
var
   age : Integer;
   teenager : Boolean;
begin
{ Initialise variables with some value     }
   age := ScrollBar1.Position;
   teenager := false;
{ Test the value of the age variable       }
{ and set the teenager variable to         }
{ True if age is between 13 and 19         }
   if (age > 12) and (age < 20) then
      teenager := true;
{ Now test the value of the teenager       }
{ variable. Display one message if it      }
{ is true, another if it is false          }
   if teenager then   { if teenager = True }
      ShowMessage('You are a teenager.')
   else               {if teenager = False }
      ShowMessage('You are no teenager!');
{========= END OF TUTORIAL CODE ========== }
end;

procedure TForm1.ScrollBar1Change(Sender: TObject);
begin
   AgeLabel.Caption := IntToStr(ScrollBar1.Position);
end;

end.
```

## Code overview
### `unit`
When you are working with code, you will be working in **units**:
- each code **file** is **unit**
- the code file begins with the unit name, which is used to identify it 

`{$mode objfpc}{$H+}` which dialect will be used


### `inteface`
Interface is a section of the Pascal program in which your various typed declaration for classes 
an other sorts of items in your code  will be defined 
#### `use`
declare elements from other files (sth like import?)
```pascal
uses
  SysUtils, Messages, Classes, Graphics, Controls,
  Forms, Dialogs, StdCtrls;
```

`var` variable
`const` constant

class
```pascal
		TForm1 = class(TForm)
		    Button1: TButton;
		    ScrollBar1: TScrollBar;
		    Label1: TLabel;
		    AgeLabel: TLabel; 
		    //...
```


### `implementation`
This is place where the actual exacutable code is written 


`begin {...} end;` you can put lines of code to be executed sequentially as a single block 
` {some code} ` without `begin end` a simple line code
`;` ends a certain expression 
`{} ` comments
`//` comments
`:=` assignment operator