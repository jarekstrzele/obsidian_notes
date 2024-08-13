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
- `xmlns="... /xaml/presentation ` zawiera definicję większości elementów XAML
- `xmlns:x="http://sc...` - w tej przestrzeni znajduje się między innymi atrybut `Name`
-  `xmlns:local="clr-namespace:KoloryWPF"` pod `local` widoczna jest przestrzeń nazw `KoloryWPF`

----
# Zdarzenie

Zmieniamy nazwy `Slider`, bo za ich pomocą będziemy zmieniać kolor prostokąta:
- `<Slider x:Name="sliderR" ...`
- `<Slider x:Name="sliderG" ...`
- `<Slider x:Name="sliderB" ...`

Podwójne kliknięcie na kontrolkę `Slider` tworzy metodę
- `Stroke` obramowanie
- `Fill` - wypełnienie
```c#
private void sliderR_ValueChanged(object sender, RoutedPropertyChangedEventArgs<double> e)
{
    rectangle.Fill = Brushes.GreenYellow;
}
```


zamykanie okna:
- dodanie atrybutu ` KeyDown="Window_KeyDown"` do `<Window>` , wartość tego atrybutu to nazwa metody, która powstała 
- kliknięcie na `KeyDown` + F12 przeniesie do metody:

```c# 
private void Window_KeyDown(object sender, KeyEventArgs e)
{
    if (e.Key == Key.Escape) Close();
}
```

ZMIANA konstruktura:
```c#
 public MainWindow()
 {
     InitializeComponent();
     // Ustawienie domyślnego koloru prostokąta na czarny
     rectangle.Fill = Brushes.Black;
     // Zaktualizowanie koloru prostokąta przy starcie aplikacji
     sliderR_ValueChanged(null, null);
 }
```

ZMIANA METODY
```c#
 private void sliderR_ValueChanged(object sender, RoutedPropertyChangedEventArgs<double> e)
 {
     // Tworzenie nowego koloru na podstawie wartości suwaków
     System.Windows.Media.Color kolor = System.Windows.Media.Color.FromRgb(
         (byte)sliderR.Value,
         (byte)sliderG.Value,
         (byte)sliderB.Value);

     // Ustawienie koloru prostokąta na nowo utworzony kolor
     rectangle.Fill = new SolidColorBrush(kolor);
 }

```


#wpf/brushes 
>[!important] `Brushes`
>- klasa Statyczna z `System.Windows.Media` ma wbudowane, statyczne właściwości reprezentujące predefiniowane pędzle `Brush`
>- każda z właściwości klasy `Brushes` jest obiektem `SolidColorBrush`, który  reprezentuje jednolity kolor













