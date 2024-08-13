[[_ I część - Wzorzec MVVM. Podstawy XAML]]

> Proponuję zbudować prostą aplikację, w której za pomocą trzech suwaków kontrolować będziemy kolor widocznego w oknie prostokąta.


# N O W Y PROJEKT

"Zakotwiczenie" kontrolek do brzegu okna 

![[Pasted image 20240813203159.png]]


```xml
<Window x:Class="KoloryWPF.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:KoloryWPF"
        mc:Ignorable="d"
        Title="MainWindow" Height="320" Width="800">
  <Grid>
      <Rectangle Fill="#FFF4F4F5" Margin="10,10,10,91" Stroke="Black"/>
      <Slider x:Name="slider" Margin="10,0,10,64" Height="22" VerticalAlignment="Bottom"/>
      <Slider x:Name="slider1" Margin="10,0,10,37" Height="22" VerticalAlignment="Bottom"/>
      <Slider x:Name="slider2" Margin="10,0,10,10" Height="22" VerticalAlignment="Bottom"/>
  </Grid>


</Window>
```


## `x:Class=`
ten kod `<Window x:Class="KoloryWPF.MainWindow" ...` łączy plik `MainWindow.xaml` z klasą `C#` o nazwie `MainWindow` w pliku `MainWindow.xaml.cs`

## `xmlns`
ten atrybut określa domyślną przestrzeń nazw używaną w bieżącym elemencie XAML:
- `... /xaml/presentation ` zawiera definicję większości elementów XAML
- 


