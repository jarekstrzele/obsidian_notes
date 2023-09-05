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



