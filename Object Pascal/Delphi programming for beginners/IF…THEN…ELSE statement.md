[[_ 0 intro]]

# Conditional Execution in Program. IF…THEN…ELSE statement

```pascal
	If <logical expression> Then
		<statement 1>
	Else
		<statement 2>;
```
Given two integer numbers, compute the maximum value of them.
```pascal
procedure TfrmMy.btnMaxClick(Sender: TObject);
var
	a, b, m: integer;
begin
	a:=StrToInt(edtA.Text);
	b:=StrToInt(edtB.Text);
	if a>b then
		m:=a
	else
		m:=b;
	lblMax.Caption:=IntToStr(m)
end;

```
>[!important]
>It should be noted that the `If…Then…Else` statement ==does not need a
semicolon before the Else keyword==, because it is a single complex statement,
and there cannot be Else without If.

### compound statment
A compound statement consists of several statements enclosed in the operator brackets
begin…end.

```pascal
If x<0 Then
begin
	y:=1;
	k:=k+1;
end
Else
begin
	y:=2*x;
	k:=x;
end;
```

Exercise 1.
Two integers $m$ and $n$ are entered by the user. If $n$ is divisible by $m$, then the result of the division of $m$ by $n$ should be displayed. Otherwise the program should display the message “n cannot be divided by m”.
```pascal

procedure TForm2.btn1Click(Sender: TObject);
Var
  a: Integer;
  b: Integer;
begin
   a := StrToInt(edtN.Text);
   b := StrToInt(edtM.Text);

   if (a mod b) = 0 then
    lblResult.Caption := IntToStr(a div b)
   else
    lblResult.Caption := 'Nie da się ';
end;

```
## Nested If
```pascal
If <logical expression 1> Then
	<statement 1>
Else
	If <logical expression 2> Then
		<statement 2>
	Else
		<statement 3>;
```

## Nested compound If
```pascal
If <logical expression 1> Then
begin
	<statement 1>
	If <logical expression 2> Then
begin
	<statement 2>
	<statement 3>
end
```

