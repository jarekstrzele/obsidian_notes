[[_ 0 intro]]

# Variables and Types of Variables. Type Conversion


## Assignment operator
### `:=`
`<variable name>:= <expression>;`

> The way it works internally is that the value of the expression on the
right of the assignment operator is calculated first, and then that resulting
value is assigned to the variable on the left of the assignment operator.

## variable
==variable== a location in memory tha has a name
`<variable name>:= <expression>;`
A name ==is not case sensitive==
```pascal
Var
	<variable name>: <data type>;
```


```pascal
procedure TfrmMy.btnMyClick(Sender: TObject);
Var
	k: Integer;
begin
end;
```

## arithmetic
`+ - / *`

`/` division Real,Integer => Real
`Div` division Integer => Integer
`Mod` remider of Integer division

```pascal
ementation

{$R *.dfm}

procedure TForm2frmCalcAdd.btnAddClick(Sender: TObject);

Var
    a,b,c: Single;

  begin
    a:=StrToFloat(edtA.Text);
    b:=StrToFloat(edtB.Text);
    c:=a+b;
    lblResult.Visible:=true; //make label with answer visible
    lblResult.Caption:=FloatToStr(c); // set the value of th answer to the label

    lblAnswer.Caption := edtA.Text + ' + ' + edtB.Text + '=' + FloatToStr(c);


  end;

procedure TForm2frmCalcAdd.btn_addClick(Sender: TObject);
begin
Var
  a,b,c: Single;
  a := StrToFloat(edtA.Text);
  b := StrToFloat(edtB.Text);
  c := a + b;
  lblResult.Visible:= true;
  lblResult.Caption := FloatToStr(c);

   lblAnswer.Caption := edtA.Text + ' + ' + edtB.Text + ' = ' + FloatToStr(c);
  end;

procedure TForm2frmCalcAdd.btn_multiClick(Sender: TObject);
begin
Var
  a,b,c: Single;
  a := StrToFloat(edtA.Text);
  b := StrToFloat(edtB.Text);
  c := a * b;
  lblResult.Visible:= true;
  lblResult.Caption := FloatToStr(c);
  lblAnswer.Caption := edtA.Text + ' * ' + edtB.Text + ' = ' + FloatToStr(c);

end;
end.
```




















