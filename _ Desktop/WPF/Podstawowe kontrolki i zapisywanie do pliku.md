#wpf/controls 

Podstawowe kontrolki WPF (Windows Presentation Foundation), które są często używane do budowy formularzy, to między innymi TextBox (pole tekstowe), Button (przycisk), CheckBox (pole wyboru), RadioButton (przycisk opcji), ComboBox (lista rozwijana), Label (etykieta) oraz ListBox (lista wyboru). Poniżej opiszę każdą z tych kontrolek wraz z przykładem kodu, pokazując, jak je zaimplementować w aplikacji WPF z użyciem C#.

> `Content` jest ogólnym terminem używanym w WPF do określenia zawartości, którą można umieścić wewnątrz kontrolki, takiej jak `RadioButton`. Może to być prawie cokolwiek, ponieważ `Content` przyjmuje obiekt typu `object`. Możesz umieścić w nim tekst, obraz, panel z kolejnymi kontrolkami lub nawet niestandardowy układ kontrolki złożony z wielu elementów. To bardzo elastyczna funkcjonalność, która pozwala na rozbudowaną personalizację interfejsu użytkownika.


# KONTROLKI


### 1. TextBox (Pole tekstowe)

Służy do wprowadzania lub wyświetlania jednoliniowego tekstu.

xamlCopy code

`<TextBox Name="textBoxExample" Width="200" Margin="10"/>`

Obsługa w C# (np. pobieranie tekstu):

csharpCopy code

`string text = textBoxExample.Text;`

### 2. Button (Przycisk)

Używany do wyzwalania akcji po kliknięciu.

xamlCopy code

`<Button Name="buttonExample" Content="Kliknij mnie" Width="100" Margin="10" Click="buttonExample_Click"/>`

Obsługa w C# (definicja metody obsługującej kliknięcie):

csharpCopy code

`private void buttonExample_Click(object sender, RoutedEventArgs e) {     MessageBox.Show("Przycisk został kliknięty!"); }`

### 3. CheckBox (Pole wyboru)

Pozwala na wybór jednej lub więcej opcji.

xamlCopy code

`<CheckBox Name="checkBoxExample" Content="Akceptuję warunki" Margin="10"/>`

Obsługa w C# (sprawdzanie stanu):

*null-coalescing* 
`bool isChecked = checkBoxExample.IsChecked ?? false;`

> W WPF, właściwość `Content` kontrolki, takiej jak `CheckBox`, jest typu `object`. Oznacza to, że może przechowywać dowolny typ danych, nie tylko ciągi znaków. Gdy chcesz wyświetlić zawartość kontrolki `CheckBox` w kontrolce takiej jak `MessageBox`, musisz zapewnić, że wartość, którą próbujesz wyświetlić, jest ciągiem znaków (`string`).



### 4. RadioButton (Przycisk opcji)

Umożliwia wybór jednej opcji z grupy.

```xml
<RadioButton Name="radioButton1" Content="Opcja 1" GroupName="Group1" Margin="10"/> 
<RadioButton Name="radioButton2" Content="Opcja 2" GroupName="Group1" Margin="10"/>
```

## Obsługa w C# (sprawdzanie wybranej opcji):

### przez `if`
```c#
if iiadioButton1.IsChecked == true) {     
// Opcja 1 została wybrana 
} else if (radioButton2.IsChecked == true) {     
// Opcja 2 została wybrana 
}
```

### przez Ustawienie wspólnego obsługiwancza zdarzeń

```xml
<RadioButton Name="radioButton1" Content="Opcja 1" GroupName="Group1" Checked="RadioButton_Checked" />
<RadioButton Name="radioButton2" Content="Opcja 2" GroupName="Group1" Checked="RadioButton_Checked" />
<RadioButton Name="radioButton3" Content="Opcja 3" GroupName="Group1" Checked="RadioButton_Checked" />

```

```c#
private void RadioButton_Checked(object sender, RoutedEventArgs e)
{
    var radioButton = sender as RadioButton;
    if (radioButton != null)
    {
        // Wykonaj działanie w zależności od wybranego RadioButton
        MessageBox.Show($"Wybrano opcję: {radioButton.Content}");
    }
}

```

### przez użycie `Tag`
```xml
<RadioButton Name="radioButton1" Content="Opcja 1" Tag="1" GroupName="Group1" Checked="RadioButton_Checked" />
<RadioButton Name="radioButton2" Content="Opcja 2" Tag="2" GroupName="Group1" Checked="RadioButton_Checked" />

```

```c#
private void RadioButton_Checked(object sender, RoutedEventArgs e)
{
    var radioButton = sender as RadioButton;
    if (radioButton != null)
    {
        string tagValue = radioButton.Tag.ToString();
        // Wykonaj działanie w zależności od wartości Tag
        MessageBox.Show($"Wybrano opcję o tagu: {tagValue}");
    }
}

```
 



### 5. ComboBox (Lista rozwijana)

Umożliwia wybór jednej opcji z rozwijanej listy.

```xml
<ComboBox Name="comboBoxExample" Margin="10">     
	<ComboBoxItem Content="Opcja 1"/>     
	<ComboBoxItem Content="Opcja 2"/>     
	<ComboBoxItem Content="Opcja 3"/> 
</ComboBox>
```

Obsługa w C# (pobieranie wybranej opcji):

csharpCopy code

```c#
var selectedItem = comboBoxExample.SelectedItem as ComboBoxItem; 
string selectedContent = selectedItem.Content.ToString();
```

### 6. Label (Etykieta)

Służy do wyświetlania tekstów, które nie są przeznaczone do edycji przez użytkownika.



`<Label Content="To jest etykieta" Margin="10"/>`

Obsługa w C# nie jest potrzebna, gdyż Label służy głównie do wyświetlania stałego tekstu.

### 7. ListBox (Lista wyboru)

Pozwala na wybór jednego lub więcej elementów z listy.


```xml
<ListBox Name="listBoxExample" Margin="10">     
	<ListBoxItem Content="Element 1"/>     
	<ListBoxItem Content="Element 2"/>     
	<ListBoxItem Content="Element 3"/> 
</ListBox>
```

Obsługa w C# (pobieranie wybranych elementów):
```c#
foreach (ListBoxItem item in listBoxExample.SelectedItems) { 

	string content = item.Content.ToString();     
// Przetwarzanie wybranych elementów 
}
```

8. *DataPicker*

`d` - short date pattern - krótki format daty
`D` - długi format daty
`t` - krótki format czasu
`T` - długi format czasu




### 8. Praca z obrazkiem `<Image>`

- w projekcie zrób folder `Resources`, do którego skopiuj obrazki
- we właściwościach każdego obrazka `Build Action` ustaw na `Resource`
	- `Build Action` określa, jak dany plik jest traktowany podczas procesu budowania (kompilacji) aplikacji.
	- Gdy ustawisz `Build Action` pliku obrazu na `Resource` w projekcie WPF, oznacza to, że obraz zostanie włączony do głównego pliku wykonywalnego aplikacji (EXE) lub biblioteki (DLL) jako zasób.

#### `<Image Source="pack://application:,,,/Resources/example.jpg" Width="100" Height="100"/>`

wyjaśnienie:
- `pack://application:,,,` - Wskazuje, że zasób jest pakietem wbudowanym w aplikację.
- `/` - Początek ścieżki względem głównego katalogu projektu.
- `Resources/example.jpg` - Ścieżka względna do pliku wewnątrz projektu.


Ustawienie obrazu jako tła:





--------------
# Zapisywanie i odczytywanie danych.
#serialization

## przygotowanie danych
dane najwygodniej zapisać jako obiekt

```c#
public class FormData
{
    public string Name { get; set; }
    public string Email { get; set; }
    // Dodaj więcej pól zgodnie z formularzem
}

```


## zapis

### do pliku tekstowego
```c#
public void SaveDataToTextFile(FormData data, string filePath)
{
    string content = $"Name: {data.Name}\nEmail: {data.Email}";
    File.WriteAllText(filePath, content);
}

```

### xml

Do zapisu danych w formacie XML można wykorzystać `System.Xml.Serialization.XmlSerializer`:

```c#
public void SaveDataToXmlFile(FormData data, string filePath)
{
    XmlSerializer serializer = new XmlSerializer(typeof(FormData));
    using (StreamWriter writer = new StreamWriter(filePath))
    {
        serializer.Serialize(writer, data);
    }
}

```

### json
Do zapisu danych w formacie JSON można użyć `System.Text.Json.JsonSerializer` (dostępne od .NET Core 3.0 i nowszych wersji):

```c#
public void SaveDataToJsonFile(FormData data, string filePath)
{
    string json = JsonSerializer.Serialize(data);
    File.WriteAllText(filePath, json);
}

```


### cvs

```c#
public void SaveDataToCsvFile(FormData data, string filePath)
{
    string csvLine = $"{data.Name},{data.Email}";
    // Dodaj nagłówek, jeśli plik jest tworzony od nowa
    // string header = "Name,Email";
    // File.WriteAllText(filePath, header + Environment.NewLine + csvLine);
    File.AppendAllText(filePath, csvLine + Environment.NewLine);
}

```
























