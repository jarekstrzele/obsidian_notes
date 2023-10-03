[[_ C Sharp od Podstaw do WPF i XAML]]


# Binding
to co wpisane w `TextBox` zostaje automatycznie przekopiowane do `TextBlock`

>[!info] zasada nieinterwencji
>kodem C# nie ingeruj w to, co dzieje się w kodzie xaml

`{}` to jest markup extension
`Path` - ścieżka, co chcemy wybrać z danego elementu
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
Potrzebujemy typu, który będzie przechowywać FUNKCJE - DELEGAT

>[!info] delegaty
> - Delegat jest to typ danych, który reprezentuje wskaźnik do metody o określonym sygnaturze.
> - Delegaty pozwalają na przechowywanie referencji do metod i wywoływanie tych metod w późniejszym czasie.
> - Są używane do implementacji mechanizmu wywoływania zwrotnego (callback) oraz obsługi zdarzeń.
> - Delegaty są deklarowane za pomocą słowa kluczowego "delegate".

```c#
public delegate void MojaMetodaDelegata(string wiadomosc);

```




`event` zdarzenie
`delegat` reprezentant jakiejś zbiorowości (sygnatura funkcji)

Tworzymy w naszej aplikacji nowy pliki
`Simulation.cs` z klasą Simulation

Simulation.cs
```c#

```


















