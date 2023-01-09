[[_ 0 intro]]
#delphi/graphics

# Graphics
## `TPaintBox`
Drawings will be placed into TPaintBox object (in Additional Palett)

To compute the center of the TPaintBox:
```pascal
x0:= pbxEx.Width div 2;
y0:= pbxEx.Height div 2;
```
`pbxEx` the name of TPaintBox component

```pascal
pbxEx.Canvas.Pen.Color:=clRed;
pbxEx.Canvas.Pen.Width:=3;
```

To fill the inner space of closed figures `Brush`
`pbxEx.Canvas.Brush.Color:=clGreen;`

```pascal
procedure TForm6.Button1Click(Sender: TObject);
begin
                   PaintBox1.Canvas.LineTo(10, 500)       ;
       PaintBox1.Canvas.Pen.Color:=clRed ;
       PaintBox1.Canvas.Pixels[30, 40]:=clRed;
       PaintBox1.Canvas.MoveTo(500,200) ;

        PaintBox1.Canvas.Rectangle(550,10,0,0) ;
         PaintBox1.Canvas.MoveTo(100,500) ;
        PaintBox1.Canvas.Ellipse( 10,20,500,500) ;
end;

```







