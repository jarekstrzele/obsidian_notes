[[_ 0 intro Delphi Object Pascal]]


# loops and arrays

## `for`
```pascal
procedure TForm1.FormCreate(Sender: tObject);
var 
	i : integer ;
begin 
	for i := 0 to 255 do
		ListBox1.Items.Add('Ascii ' + IntToString(i) + ' = ' + Chr(i)) ;
		// ListBox1.Items.Add(Format('%s %d = ''%s''', [s,i, UTF8Encode(string(Char(i)))])) ;
end;

```

## `case`
```pascal
procedure TForm1.Button1Click(Sender: TObejct);
var
	i : integer;
	s : string ;
begin
	ListBox1.Clear;
	for i := 0 to 255 do
	begin
		s := '' ;
		case (i) of
			48..57: s := 'Number : ' ;
			65..90, 97..122: s := 'Letter: ' ;
			else s := 'Speciall : ' ;
		end;
		ListBox1.Items.Add( Format('%s %d = ''%s''', [s, i, UTF8ENcode(string(Chr(i)00]00 ;))]))
	end;
end;

```

## `while` and `repeat`
```pascal
var
	i : integer ;
begin
	ListBox1.Clear ; 
	i:= 0 ;
	while (Memo1.Lines.Count > i) do
	begin
		ListBox1.Items.Add(Memo1.Lines[i]) ;
		i := i + 1 ;
	end
end ;
```

```pascal
	repeat
		ListBox1.Items.Add(memo1.Lines[i]);
		i := i + 1 ;
	until i = Memo1.Lines.Count ;

```


---
## Arrays
It is just a sequential list o some sorto of data items

`var	<name> : array[<index1>..<index2>] od <type> ;`

4 string items:
`var sarray : array[1..4] of string ;`
`var sarray : array[0..3] of string ;`

`saraay[1]='one' ;`
```pascal
const
	InitArray : array[1..4] of string = ('un', 'deux', 'trois','quatre' ) ;
```


