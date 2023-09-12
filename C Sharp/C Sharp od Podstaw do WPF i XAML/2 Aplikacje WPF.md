#wpf

>[!info] WPF *Windows Presentation Foundation*
framework Microsoftu do tworzenia aplikacji desktopowych

>[!info] XAMPL *eXtensible Application Markup Language*
>język bazujący na XML
>`<nazwa_tagu atrybut="dodatkowa_informacja"> zawartość </nazwa_tagu>`
>łatwy sposób opisania kontrolek


#### `Visual Studio> Aplikacja WPF`

powiązanie xaml z bibliotekam 
```xaml
<Window x:Class="WpfApp1.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
```
`xmlns` xml namespace

`xmlns:x`  - `x` z przestrzeni nazw `xmlns`

`<Window x:Class="WpfApp1.MainWindow"` okno Window będzie miało w kodzie klasę o nazwie `WpfApp1.MainWindow`

Jeżeli do okna dodasz buttona, to podwójne kliknięcie na niego, automatycznie wygeneruje metodę obsługującą kliknięcie.
do atrybutu buttona zostanie dodany ` Click="btn1_Click"` czyli `btn1_Click` jest nazwą funkcji wygenerowanej automatycznie
 
nazwa projektu >bin>Debug>net6.0 > tu jest plik exe dla naszej aplikacji

w `App.xaml`:
```xaml
<Application x:Class="WpfApp1.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:local="clr-namespace:WpfApp1"
             StartupUri="MainWindow.xaml">

```

 `StartupUri="MainWindow.xaml">`  od czego ma zacząć się aplikacja


zmiana nazw przez `refactor` z menu podręcznego


---
# Najważniejsze pojęcia

w `xaml` `<...>` to znacznik, gałąź, więzeł, bo cały dokument xamla jest jak HTML - jedno zwiera się w drugim
relacja `rodzic <--> dziecko`

skrót `ctr+alt+x` otwiera Toolbox/Przybornik


Instalaca programu do podglądania struktury i logiki aplikacji WPF: *Snoop* https://github.com/snoopwpf/snoopwpf
#snoop 
	- ale wcześniej potrzebujemy menadżera do instalowania pakietów na Windows https://chocolatey.org/install#individual
	- `choco install snoop` (jako administrator)
Rodzicem na szczycie jest `<Application> ... </Aplication>`
	Ten rodzic ma trybut `StartupUri="MainWindow.xaml`, który uruchamia nasze okno


DODAWANIE ELEMENTÓW do OKIENKA:
- w kodzie `xaml`
- przez Przybornik (Toolbox)
- bezpośrednio w kodzie `.cs`:
	- nazwij znacznik w xaml np. `<Grid x:Name = "siatka" ....`
 > Atrybut `x:Name` służy do nadawania nazw elementom w interfejsie użytkownika, aby można było do nich odwoływać się programowo w kodzie C#.

	 - w pliku `MainWindow.xaml.cs`
	 - 
```c#
	InitializeComponent();

// add (raczej tak  nie rób)
	Button b1 = new Button() ;
	b1.Content = "Nowy baton" ;
	siatka.Children.Add(b1) ;

```

## mała apka podsumowując
- nowy projekt
- `<Button>` może mieć tylko jedno dziecko, więc jeżeli chcesz mieć wewątrz dwa elementy musisz je opakować w np. `<Grid>`

`MainWindow.xaml`
```c#
<Window x:Class="WpfApp2.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp2"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
    <Grid>
        <Button Click="MainButtonHandler" HorizontalAlignment="Left" Margin="140,56,0,0" VerticalAlignment="Top" Height="216" Width="504">
            <Grid  >

                <Image Height="58" Width="148" Source="/images/happy_kolor.jpg" Margin="5,-60,-5,60" />
                <Button Content="JEDEN" Height="58" Width="148" Margin="-126,46,126,-46"/>
                <Button Content="d w a ;" Height="58" Width="148" Margin="153,46,-153,-46"/>

            </Grid>

        </Button>
        <TextBlock x:Name="tekstBlok" HorizontalAlignment="Left" Margin="192,353,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Height="46" Width="116"/>

    </Grid>
</Window>

```

oraz metoda obsługująca `MainWindows.xaml.cs`
- (podwójne kliknięcie na główny klawisz)
```c#
private void MainButtonHandler(object sender, RoutedEventArgs e)
{
    tekstBlok.Text = "To kliknąłeś główny klawisz";
}
```

kliknięcie dowolnego button powoduje wywołanie metody MainButtonHandler (bo C# poszukuje obsługiwania do rodzica, do rodzica rodzica ....)

dodanie nowej metody, która będzie przypisana do wewnętrznego buttona wcale nie zatrzymije wywołani metody głównego buttona

dodajemy do `Main ... .cs`
```c#
 private void Button_Click_Dwa(object sender, RoutedEventArgs e)
 {
     MessageBox.Show("Kliknąłeś drugi baton");
 }
```

oraz zmieniamy w `Main ... .xaml`
```xaml
<Button Content="d w a " Height="58" Width="148" Margin="153,46,-153,-46" Click="Button_Click_Dwa"/>

```








