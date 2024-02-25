[[_ The Windows Presentation Foundation WPF Giode for beginners]]

```xml
 <Grid>
     <Button>
         <Button.Width>200</Button.Width>
         <Button.Height>100</Button.Height>
         <Button.FontSize>24</Button.FontSize>
         <Button.Content>
             <WrapPanel>
                 <TextBlock Foreground="Blue">Mutli</TextBlock>
                 <TextBlock Foreground="Red">Color</TextBlock>
                 <TextBlock Foreground="White">Button</TextBlock>
                 
             </WrapPanel>
            
         </Button.Content>
     </Button>

 </Grid>
```

The same effect but in C#:
```c#
      public MainWindow()
      {
          InitializeComponent();
          Grid grid = new Grid();
          this.Content = grid;
          Button btn = new Button();
          btn.FontSize = 26;
          btn.Width = 200;
          btn.Height = 100;

          WrapPanel btnWrap = new WrapPanel();
          TextBlock txtBlock = new TextBlock();
          txtBlock.Text = "Multi";
          txtBlock.Foreground = Brushes.Blue;

          TextBlock txtBlock2 = new TextBlock();
          txtBlock2.Text = "Color";
          txtBlock2.Foreground = Brushes.Red;

          TextBlock txtBlock3 = new TextBlock();
          txtBlock3.Text = "Button";
          txtBlock3.Foreground = Brushes.White;

          btnWrap.Children.Add(txtBlock);
          btnWrap.Children.Add(txtBlock2);
          btnWrap.Children.Add(txtBlock3);

          btn.Content = btnWrap;
          grid.Children.Add(btn);


      }
```


------
# StackPanel, ListBox, Visual and Logical Tree

#wpf/stackpanel #wpf/listbox













