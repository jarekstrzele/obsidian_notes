[[_ 0 intro Delphi Object Pascal]]



# Procedures and Functions
### Procedure
```pascal
implementation

{$R *.lfm}

{ TForm1 }

procedure ShowErrorMsg;
begin
  ShowMessage('You must enter your name!');

end;

procedure TForm1.btnHelloClick(Sender: TObject);
var sName : String ;
begin
     if edtName.Text = '' then
        ShowErrorMsg
     else
       sName := edtName.Text ;
       ShowMessage('Hello ' + sName)

end;

procedure TForm1.btnGoodbyeClick(Sender: TObject);
var sName : String ;
begin
    if edtName.Text = '' then
        ShowErrorMsg // wywołanie procedury choć nie ma `()`
     else
       sName := edtName.Text ;
       ShowMessage('Goodby ' + sName)

end;               
```

When you send agruments, remember about the correct number of args and the correct data types of args


### Function
```pascal
{ old version
function MsgFunc(greeting, username : string) : string;
// greeting and username can be used only inside this func
begin
   if username = '' then
       MsgFunc := 'You must enter a name'
   else
     MsgFunc := gretting + username ;
end;
 }

{ modern version }
function MsgFunc(greeting, username : string) : string;
// greeting and username can be used only inside this func
var msg : String;
begin
   if username = '' then
       msg := 'You must enter a name'
   else
     msg := greeting + username ;
   // it can be only one place inside the func
   // to use `result`
   result := msg ; // the key word `result`
end;     
```

## Passign args by value and by reference

### passing by value - non var params
s1 is a local variable and exists only in this procedure
s1 copies a value
```pascal
procedure myProc ( s1 : String ) ;
begin
	s1 := s1 + "!!!" ;
end;
```


### passing by reference - var params
s1 that is a reference to the original variable
```pascal
procedure myProc2( var s1 : string) ;
begin
	s1 := s1 + !!!;
end;

```

## Calculating interest rates




