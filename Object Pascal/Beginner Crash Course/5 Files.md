[[_  0 Full Beginner Crash Course]]

RichEdit (`redOutput`), Button
```pascal
procedure TForm6.btnFClick(Sender: TObject);
begin
 redOutput.Lines.Clear ;
 redOutput.Lines.LoadFromFile('test1.txt') ;

end;
```


Two RichEdit (one for junior, one for senior) and one button
One Gamers.txt
```txt
Josh Hendrics,18
Linus Xum,16
Kai Maggi,21
Lilly Zeller,10

```


```pascal
procedure TForm6.btnFClick(Sender: TObject);
var
  tFile : textfile ;
  sLine, sName : string ;
  iPos, iAge: integer ;
begin
  redOutputJunior.Lines.Clear ;
  redOutputSenior.Lines.Create ;

  redOutputJunior.Lines.Add('Junior Gamers' + #13 + #13) ; //#13 = enter
  redOutputSenior.Lines.Add('Senior Gamers') ;

  AssignFile(tFile, 'Gamers.txt') ;

  try
    Reset(tFIle) ; //this moves the cursor to the top of the file
  except
    showMessage('Could not find "Gamers.txt') ;
    exit ;
  end;

 while not eof(tFile) do
   begin
     ReadLn(tFile,sLine) ;
     iPos := Pos(',', sLine) ; // find the position `,` in that Line
     sName := Copy(sLine, 1, iPos-1) ;
     Delete(sLine, 1, iPos) ;
     iAge := StrToInt(sLine) ;

     if iAge >= 18  then
        begin
          redOutputSenior.Lines.Add(sName + '(' + IntToStr(iAge) + ')' ) ;

        end else
        begin
          redOutputJunior.Lines.Add(sName + '(' + IntToStr(iAge) + ')' ) ;
        end;


   end;

   CloseFile(tFile) ;
end;
```



# Write to a file
to close a window with a button.
in click handler of the button
`Form2.Close ;`

username, password, and log button amd quit button

```pascal

procedure TForm6.btnLogClick(Sender: TObject);
var
  sName, sTime, sDate, sLog: string ;
  tFile: textfile ;
begin
 sName := edtName.Text ;
 sDate := DateToStr(Date()) ;
 sTime := TimeToStr(Time()) ;
 sLog := sName + '#' + sDate + '#' + sTime ;

 AssignFile(tFile, 'log.txt') ;
 //Rewrite(tFile) ; // delete all from the file
 Append(tFile) ; // add a new item to the file
 Writeln(tFile, sLog);
 CloseFile(tFile) ;
end;

procedure TForm6.btnQuitClick(Sender: TObject);
begin
  Form6.Close ;
end;
```
















