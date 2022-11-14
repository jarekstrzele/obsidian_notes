#delphi 

https://www.youtube.com/watch?v=4MeiMJoSCJk&list=PLxAS51iVMjv8tU5VcNHvfjyJ94LR47sin

# Functions and Procedures

Functions | Procedures
-- | --
IntToStr <br> `sNum := IntToStr(10)`| Inc <br> `Inc(iCount)`
InputBox <br> `sName := InputBox('1','2','3')` | Showmessage <br> `Showmessage('Hello')`
Copy <br> `sTemp:=Copyt(sName,1,3)`| Delete <br> `Delete(sName, 4, 2)`
EOF <br> `while NOT EOF(f) do`| AssignFIle <br> `AssignFile(F, 'Data.txt')`
Function return ONE value | Procedures are just called

## Custom Delphi Functions

input -> Function -> ONE output

1. Declare your function
######  `function <function name> (params): return type ;`
```pascal
interface

uses
	WIndows, ...
type
	TForm1 = class(TForm)
	btnFunction1: TButton;
	procedure btnFunction1Click(Sender: Object): Integer; //declaration
function Max3(a,b,c : Integer) : Integer;
```

2. Write the code of the function
`ctl+shift+c`, it works if you declared a new procedure correctly

3. Use your function



















