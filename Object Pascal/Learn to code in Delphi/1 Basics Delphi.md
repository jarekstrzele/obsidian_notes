 #delphi #youtube 
 [#MrLongEducation](https://www.youtube.com/hashtag/mrlongeducation)
 

https://www.youtube.com/watch?v=h31zNbGO6A8&list=PLxAS51iVMjv_Y6gmE2DIkUCmDKOcwjHI8
https://www.youtube.com/watch?v=h31zNbGO6A8&t=0s

# Delphi start
Wen you save  a Delphi project, you save a lot of files.
Choose: `File > Save Project As`.
To avoid confilict: each project in a particular folder:
- save `someName.pas`
- and next project file in the same folder
- when you make some changes, `save all`

to close a Project choose `close all` in File
to open find your folder and chose a smaller file 


## Objects and Properties
https://www.youtube.com/watch?v=b1GGIutQVug&t=0s
>[!info] object
>Object is  the parts of a program that allow you to interact with other elements of a program or perform specific actions

>[!info] class
>A Class is the blueprint of an object.
>It describes the attributes if an object *PROPERTIES* and what the object can do *METHOD*

IN DELPHI
- `Form1` is an object of the class `t form`
- naming:
	- names must be UNIQUE
	- no spaces
	- start with a letter
	- no special characters
	- key word
	- use athree/four letter prefix in front fo the name to tell what type of component or object  it is
		- Form -> so name `frmMain`
		- TButton object -> `btnCalculate`
		- TShape -> `shpFace`
	- 
## Structure of a statemetn
`what you want to change := new value ;`

---
> Change properties in Object Inspector
> `<DESIGN TIME>`

>Change properties using code
>`<Runtime>`

---
The `exe` program is
`C:\Users\jarek\Documents\Embarcadero\Studio\ZYoutube\First\Win32\Debug`

----
```pascal
procedure TForm5.Button1Click(Sender: TObject);
begin
  shpT1.Brush.Color:= clGreen;
  shpT1.Width:= shpT1.Width + 5;
  shpT1.Shape:=stEllipse;
  shpT1.Top := shpT1.Top + 10;

end;
```

----
## SOME comon properties
1. `height/width` size of component
2. `top/left` position of the component
3. `font` apearance of the displayed text:
	1. `size`
	2. `color`
	3. `name`
4. `visible` true for seen, false for invisible
5. `hint` text displayed whan mouse is over component
	1. `showHint` set to true for the hint to be seen

----
## LABEL
#delphi/label
`lblName` 

----
## Edit
When you want to get text from the user
`edtName`
`Text` 

----
## SpinEdit
When you want to get an integer from the user (Sample palette)
`Name` -> `sedName`
`Value` number that is inside the spi edit
`maxvalue/minvalue`

---
## Variables
It is a invisible boc that stores one piece of data.
It has  to have a unique name.
It only store apraticular type of data.

### data type
- `string` can store any series of characters 
	- example: `'Helo 123#'`
	- naming: prefix `s`, e.g. `sPassword`
- `char`
	-  example `L`
	- naming: prefix `c`, e.g. `cCode`
- `integer` can store any positive or negative WHOLE number 
	- example -2,147,483,648 -- 2,147,483,647
	- naming: prefix `i`, e.g. `iScore`
-  `real` any pos or neg DECIMAL number
	- example: 43.234
	- naming: prefix `r`, e.g.  `rAverage`
- `boolean`
	- `true  /  false`
	- naming: prefix `b`, `bRegistered`

### declare
```pascal
// declare your variables
var sPassword, sUserName, sFullname : string ;
	cCode : char ;
	iNumber : integer;
	rAverage : real ;
	bCheck : boolean;

begin
	sPasword := 'xxx' ;
	cCode := 'L';
	iNumber := 78 ;
	rAverage := 56.345 ;
	bCheck := TRUE;
end;
```

`btn` + ctr-space

---
## Comments
```pascal
// one line comment

{
	many line comment
	many line comment
}
```
----
## IPO - input->Process->Output

**INPUT**: get values from components (edit boc or spin edit) and put them into variable
**PROCESS** calculate answers, using variables, and put answers into separate variables
**OUTPUT** put the answers (variables) into components (label or edit box) for them to be displayed

``
`FloatToStr(rAns)`
`FloatToStrF(real, format, integer-left., integer-right.) `
format: 
	- ffNumber
	- ffCurency
	- ffExponent
	- ffGeneral
	- ffFixt

`FloatToStrF(12345.5678, ffFixt, 2,3)` -> `'12345.567'`

## InputBox and ShowMsg
### `inputBox('a', 'b', 'c')`
`'a'` title
`'b'` label
`'c'` msg inside the boc
It works like Python `input` function, returns a string.

### `ShowMessage('some msg')`
It works like JS pop windows

```pascal
procedure TForm5.btn1Click(Sender: TObject);
var
  sName : String ;

begin
 sName :=   InputBox('Name', 'Please enter your name: ',  '') ;
    Showmessage('Hello ' + sName) ;
end;

end.
```

----
# Errors
## syntax error
- break the tules of the programming language 
-  program will not run

## logical error
- program will run and compile
- results will not be correct
- instructions given were incorrect in logic

## runtime error
- program will run and compile
- the program or user does something that cayses the program to crash




