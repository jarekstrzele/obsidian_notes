#wpf/controls 



Podstawowe kontrolki WPF (Windows Presentation Foundation), które są często używane do budowy formularzy, to między innymi TextBox (pole tekstowe), Button (przycisk), CheckBox (pole wyboru), RadioButton (przycisk opcji), ComboBox (lista rozwijana), Label (etykieta) oraz ListBox (lista wyboru). Poniżej opiszę każdą z tych kontrolek wraz z przykładem kodu, pokazując, jak je zaimplementować w aplikacji WPF z użyciem C#.

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


`bool isChecked = checkBoxExample.IsChecked ?? false;`

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


Każda z tych kontrolek ma swoje specyficzne zastosowanie i może być konfigurowana oraz stylizowana w różnoraki sposób, aby dopasować się do potrzeb aplikacji. Kod XAML odpowiada za deklarację i wizualny aspekt kontrolki, natomiast logika w C# pozwala na obsługę zdarzeń i interakcję z użytkownikiem.



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
























