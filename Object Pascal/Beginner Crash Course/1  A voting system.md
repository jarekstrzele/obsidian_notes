[[_  0 Full Beginner Crash Course]]

----
# A voting system
`FormCreate` as a `OnCreate` event
set private variable

double click on linux image:

```pascal
 private
    { Private declarations }
    iVoteLinux, iVoteWindows, iVoteApple : integer ;
  public
    { Public declarations }
  end;

var
  Form6: TForm6;

implementation

{$R *.dfm}

procedure TForm6.btnCloseClick(Sender: TObject);
begin
 Form6.Close ;
end;

procedure TForm6.btnResetClick(Sender: TObject);
begin
  iVoteLinux := 0 ;
  iVoteWindows := 0 ;
  iVoteApple := 0 ;

  pnlLinux.Caption := '0' ;
  pnlWindows.Caption := '0' ;
  pnlApple.Caption := '0' ;
end;

procedure TForm6.FormCreate(Sender: TObject);
begin
  iVoteLinux := 0 ;
  iVoteWindows := 0 ;
  iVoteApple := 0 ;

end;

procedure TForm6.imgAppleClick(Sender: TObject);
begin
   inc(iVoteApple) ;
   pnlApple.Caption := IntToStr(iVoteApple) ;
end;

procedure TForm6.imgWindowsClick(Sender: TObject);
begin
   inc(iVoteWindows) ;
   pnlWindows.Caption := IntToStr(iVoteWindows) ;
end;

procedure TForm6.imgLinuxClick(Sender: TObject);
begin
   //iVoteLinux := iVoteLinux + 1 ;
   inc(iVoteLinux) ;
   pnlLinux.Caption := IntToStr(iVoteLinux) ;

end;
```




