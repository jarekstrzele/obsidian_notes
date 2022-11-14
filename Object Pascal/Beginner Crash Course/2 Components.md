[[_  0 Full Beginner Crash Course]]

# Components

## Image

`Image` component and `Picture` property
and property `Strech` := `true` 

---
## `Inputbox`

`sName : = Inputbox('Name', 'What is your name?', '') ; `

## variable , constant

`var`
`const VAT := 0.15 ;`

---
## Checkbox
more then one can be checked
For ` CheckBox` Name: prefix `cbx`
`  if cbxContract.Checked then`

`TEdit` has a property `NUmberOnly`
`TSpinEdit`: prefix `sed`

not finished
```pascal

procedure TForm6.Button2Click(Sender: TObject);
var
  iPrice, iNumSMS : integer ;
  rFinalPrice : real ;

begin
  iPrice := StrToInt(edtCost.Text) ;
  iNumSMS := sedNumSMS.Value ;

  if cbxContract.Checked then
    begin
         if iNumSMS > 10 then
         begin
          iNumSMS:= iNumSMS - 20 ;
         end
    else
      begin
        iNumSMS:=0 ;
      end;

    rFinalPrice := (iNumSMS * iPrice) / 60 ;
    lblOutput.Caption := 'Total Price = ' + FormatFloat('R0.00', rFinalPrice) ;
    end;
end;

end.

```

## Radio button and RadioGroup
e.g. for gender
#### radiogroup - to group radiobuttons
prefix `rbg`

to add option to this group, property `Items`
and in property `ItemIndex` you can set the marked item (`-1` no one is makred)

#### to get data from radio group
`<group name>.ItemIndex`




