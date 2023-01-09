[[_ 0 intro]]



# TMemo
It is an edit box that handles multiple lines of text.

You can dynamically create `TMemo` content using its properties and methods.

## Lines Property
The text is stored in `Lines Property` and represents the numbered set of lines (index=0)
example:
```pascal
var
	s: string;
begin
	s:=memEx.lines[2]; //the valie of the 2nd line is assigned to s variable
	memEx.Lines[3]:='Hi'; // string constant 'Hi' is assigned to the 4rd line ...
```
## Count Property
Count property returns the total number of lines.
`k:memEx.Lines.Count;`

## other properties
- `wordwarp`
- `maxlength` ($0$ without limit)
- ...

## Method
### `Delete`
This method deletes the line with the specified index. Other lines will automatically be moved and renumberd
`memEx.Lines.Delete(0)`

Only leave the odd lines.
```pascal
k:= memEx.Lines.Count;
for i:= k-1 downto 1 do
	if (i mod 2) <> 0 then
		memEx.Lines.Delete(i);
```
### `Exchange`
Exchange swaps the positions of two lines with the specified indexes.

swaps 0 and 1 lines
`memEx.Lines.Exchange(0,1)`

### `Move`
This moves a line to a new position
`memEx.Lines.Move(1,5);`

### `Clear`
Completely clear Tmemo content.
`memEx.Lines.Clear`

### `add`, `append`
`append` adds a new line to the end of TMemo
```pascal
// Fill a Tmemo with numbers from 1 to 10, one number per line.
memEx.Lines.Clear ;
For i:=1 to 10 do
begin
	memEx.Lines.Append(IntToStr(i)) ;
end ;
```

`add` 
- works the same as `append`
- return the index of the new string

### `insert`
Insert a line with a specified index. Other lines will autmatically move
```pascal
// adds empty line instead of the line with index 2, which is moved, not deleted
memEx.Lines.Insert(2, ' ')
```












