#object_pascal/procedure
[[Object Pascal/Delphi programming for beginners/_ 0 intro]]


# Procedures
>[!important] to-down programming
>This principle states that the main task of any program has to be split into several subtasks. Then, every subtask should be split into even more simple subtasks and this process continued until you end up with a set of small, simple tasks that are easy to implement

==procedure== separate subtask


### procedure call syntax
#### `<procedure name> (<call parameters list>);`
```pascal

var
 A, B, C, D, X1, X2 : Real;

begin
  coefInput(A,B, C); // calling procedure coefInput
  D := sqrt(B)-4*A*C;
  if D >= 0 then
    begin
      calc(A, B, C, D, X1, X2); //calling procedure calc
      prn(X1, X2); // calling procedure prn

    end
  else
    lblNo.Visible := true;

end;

```

### procedure definition syntax
 ```pascal
 procedure <procedure name> (<formal parameterslist>); 
	 <declarations>
begin
<statements>
end;
 ```

example with **value parameters**
```pascal
Procedure Prn(Xf, Xs: real);
begin
	frmQuadEq.lblX1.Visible:=true;
	frmQuadEq.lblX1.Caption:=’x1=’+FloatToStr(Xf);
	frmQuadEq.lblX2.Visible:=true;
	frmQuadEq.lblX2.Caption:=’x2=’+FloatToStr(Xs);
end;
```

>[!important] 
>There is one-to-one correspondence between call parameters and formal parameters.
>The number, order, and types of call and formal parameters should be identical.

> We would **get an error** if we wrote `lblX1.Visible:=true`. In the **user-defined procedures**, we have to write the ==complete name of the component== (specifying to which form it belongs because there can be ==several forms== in the program, in general).


To define parameters as variables, we have to use the keyword
`var` before them. **Call parameters should be variables for the procedure’s variable parameters**:

with **variable parameters**
```pascal
Procedure coefInput(var k1, k2, k3: real);
begin
	k1:=StrToFloat(frmQuadEq.edtA.Text);
	k2:=StrToFloat(frmQuadEq.edtB.Text);
	k3:=StrToFloat(frmQuadEq.edtC.Text);
end;
```
##### `For the  values of variables to be returned from procedure to main program, we have to use variable parameters.`



with **variable parameters and value parameters**
```pascal
procedure Calc(k1, k2, dis: real; var Xf, Xs:
Real);
begin
Xf:=(–k2+Sqrt(dis))/(2*k1);
Xs:=(–k2-Sqrt(dis))/(2*k1);
end;
```
We have to return values of roots, so the formal parameters
Xf and Xs will be variable parameters. We do not need to return first and second coefficients and discriminant values. They will be passed as value parameters.

procedure without params:
```pascal
procedure Init;
begin
	frmQuadEq.lblX1.Visible:=false;
	frmQuadEq.lblX2.Visible:=false;
	frmQuadEq.lblNo.Visible:=false;
end;
```





