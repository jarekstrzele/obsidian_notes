[[_ C Sharp od Podstaw do WPF i XAML]]


# Binding
to co wpisane w `TextBox` zostaje automatycznie przekopiowane do `TextBlock`

>[!info] zasada nieinterwencji
>kodem C# nie ingeruj w to, co dzieje się w kodzie xaml

```xml
<StackPanel>
   <TextBox x:Name="textDoKopiowanie" Text="Coś zupełnie nowego" />
   <TextBlock Text="{Binding ElementName=textDoKopiowanie, Path=Text}" TextWrapping="Wrap"  Height="80"/>
</StackPanel>
```
najpierw bez `Path=Text`

`Mode=OneWay` - określa kierunek przekazywania tekstu domyślnie jest `OneWay`
```xml
    <StackPanel>
        <TextBox x:Name="textDoKopiowanie" Text="Jutro funtro" />
        <TextBlock x:Name="mojTB" Text="{Binding ElementName=textDoKopiowanie
            ,Path=Text
            ,Mode=TwoWay}" />
        <Button Content="Button" Click="Button_Click"/>
    </StackPanel>
</Window>

```

```C#
private void Button_Click(object sender, RoutedEventArgs e)
        {
            mojTB.Text = "To jest zmiania, na może lepsze!!!!!!";
        }
```

```xml
 <Slider Value="{Binding ElementName=SliderValue, Path=Text, Mode=OneWayToSource}"
         Maximum="30" Minimum="0"
         IsSnapToTickEnabled="True"
         TickFrequency="5"></Slider>
 <TextBox x:Name="SliderValue"></TextBox>
```
`Mode=OneWayToSource` zmiany w sliderze mają wpływ na TextBox, ale TextBox nie wypłwa na slidera

---------------

# Eventy i Delegaty 

Tworzymy w naszej aplikacji nowy pliki
`Simulation.cs` z klasą Simulation

Simulation.cs
```c#

```


















