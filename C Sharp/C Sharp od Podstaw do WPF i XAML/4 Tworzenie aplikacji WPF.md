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

`,Mode=OneWay` - określa kierunek przekazywania tekstu domyślnie jest `OneWay`







