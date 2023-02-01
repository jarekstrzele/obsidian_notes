
[[Object Pascal/Delphi programming for beginners/_ 0 intro]]

# Handling a Button Press Event
>[!quote]
>Visual components are able to generate and handle several dozens kinds of events: mouse click, button press, keyboard press, windows opening, etc

A program response to an event is programmed as a list of actions to be done; this list is entered in a **Code Editor** window

### Method
#### `<component_name>.<method>;`
```delphi
{$R *.dfm}

procedure TfrmButtonExample.btnMyButtonClick(Sender: TObject);
begin
    frmButtonExample.Close;
end;

end.
```

### Property
#### `<component_name>.<property>:=<newValue>;`
```delphi
{$R *.dfm}

procedure TfrmButtonExample.btnMyButtonClick(Sender: TObject);
begin
    frmButtonExample.Color:=clWhite;
end;

end.
```
on the button `btnMyButtonClick` you set a event handle: the color of backgorund of form `frmButtonExample` will be set on White

##### to assign a value form one component to another

#### `<component1_name>.<property1> := <component2_name>.<property2>;`

`lblMy.Caption:=edtMy.Text;` this instructs the program to put the text from text box `edtMy` into the caption of label lblMy
Multiple actins are separated by semicolon

```pascal
begin 
	edit1.Clear;
	edit1.Color:=clBlue; 
end;
```
```pascal
procedure TForm2.btn1Click(Sender: TObject);
begin
  lbl1.Caption := entry.Text;
  entry.Clear;
end;
end.
```







