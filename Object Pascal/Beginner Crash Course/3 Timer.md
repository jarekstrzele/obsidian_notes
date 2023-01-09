[[_  0 Full Beginner Crash Course]]

#delphi/timer
---
one panel (`pnlForm`):
	- panel
	- button
	- image
	- Timer tmrName

double click on Timer component
```pascal
procedure TForm6.tmrAnimateTimer(Sender: TObject);
var
  iRightBorder, iRightSide: integer ;
begin
  iRightSide := imgLinux.Left + imgLinux.Width ;
  iRightBorder := pnlForm.Width ;

  if (iRightSide > iRightBorder) then
  begin
    imgLinux.Left := 10 ;
  end else begin
    imgLinux.Left := imgLinux.Left + 20 ;
  end;
end;
```



