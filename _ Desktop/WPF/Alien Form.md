

# zapisywanie do pliku + TextBlock
```c#
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;
using static System.Net.Mime.MediaTypeNames;
using System.Xml.Linq;

namespace Kwestiorariusz_ufoludka
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }


        private void ZapiszDoPlikuButton_Click(object sender, RoutedEventArgs e)
        {
            try
            {
                string documentsPath = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments);
       
                string fileName = "_MOJ_plik.txt";

                //string aDocumentsSubFolderPath = System.IO.Path.Combine(documentsPath, "aSubFodler");
                string downloadsPath = Environment.GetFolderPath(Environment.SpecialFolder.UserProfile) + "\\Downloads";
                string fullFilePath = System.IO.Path.Combine(downloadsPath, fileName);

                string textToWrite = tBx.Text;

                File.WriteAllText(fullFilePath, textToWrite);

                MessageBox.Show($"Dane zostały zapisane w {fullFilePath}");
            }
            catch (Exception ex)
            {
                MessageBox.Show($"Wystąpił błąd: {ex.Message}");
            }
           
        }
    }
}


```

-------------
# ComboBox

>[!important] WAŻNE
>(ComboBoxItem)comboBox.SelectedItem`: Elementy ComboBox są domyślnie typu `object`,

```c#

// dopisujemy do głównego pliku .cs do metody obługujacej kliknięcie
 string textToWrite = $"tekst: {tBx.Text} \nComboBox: {((ComboBoxItem)cBx.SelectedItem).Content.ToString()} " ;

```

do pliku `xaml` dodałem
```xml
<StackPanel Orientation="Horizontal">
    <ComboBox x:Name="cBx" SelectedIndex="0" Margin="10">
        <ComboBoxItem Content="Opcja 1" />
        <ComboBoxItem Content="Opcja 2" />
        <ComboBoxItem Content="Opcja 3" />

    </ComboBox>
</StackPanel>

```



------
# RadioButton
ten kod dodaj do głównego `.cs` w obsłudze kliknięcia
```c#
// ....

//ComboBox:
string cBxText = ((ComboBoxItem)cBx.SelectedItem).Content.ToString();

//RadioButton
bool idRBtn1 = rBtn1.IsChecked.Value; //true, false
string idRbtnContent = rBtn1.Content.ToString();


string textToWrite = $"tekst: {tBx.Text} \nComboBox: {cBxText}\nrBtn1: {idRBtn1}, {idRbtnContent} " ;

```


GroupBox może mieć tylko jedno dziecko, więc `RadioButtons` zamknąłem w `<StackPanel>`
```xml
<StackPanel Orientation="Horizontal">

    <GroupBox Margin="20">
    <GroupBox.Header>
        Jak chcesz zostać porwany?
    </GroupBox.Header>
    <StackPanel>
        <RadioButton Name="rBtn1" >Gdy śpisz w domu</RadioButton>
        <RadioButton Name="rBtn2">Gdy jedziesz samochodem</RadioButton>
        <RadioButton Name="rBtn3" >Gdy jesteś w ubukacji</RadioButton>
    </StackPanel>
</GroupBox>

    <GroupBox Margin="20">

        <GroupBox.Header>
            Czy chcesz podróżować na inne planety?
        </GroupBox.Header>
        <StackPanel>
            <RadioButton Name="rBtnTak" >Tak</RadioButton>
            <RadioButton Name="rBtnNie">Nie</RadioButton>
            <RadioButton Name="rBtnNieWiem" >Nie wiem</RadioButton>
        </StackPanel>
    </GroupBox>

</StackPanel>
```

---
# DatePicker
```xml
  <DatePicker Name="dateAttack" Width="200" SelectedDate="2023-10-10" />
```

```c#
// DatePicker
DateTime? selectedDate = dateAttack.SelectedDate;
//string dateAttactString = selectedDate.Value.ToString();
string dateAttactString = selectedDate.HasValue ? selectedDate.ToString() : "brak daty"; //.
```

----------
# Expander
```xml
 <Expander Header="Kliknij, aby rozwijać/zawijać">
     <TextBlock Margin="5">
         Nowa treść
     </TextBlock>
 </Expander>

```

```xml
 <Expander Header="Kliknij, aby rozwijać/zawijać">
     <Border BorderBrush="Black" BorderThickness="1">
         <StackPanel>
             <TextBlock Margin="5">
         To jest zawartość rozkładanego panelu.
             </TextBlock>
             <TextBlock Margin="5">
         Nowa treść
             </TextBlock>
         </StackPanel>
     </Border>
 </Expander>
```







-----


# cały kod z bezpośrednim zapisywaniem do pliku
```c#
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;
using static System.Net.Mime.MediaTypeNames;
using System.Xml.Linq;
using Microsoft.Win32; // Dodaj odpowiednie using dla OpenFileDialog i SaveFileDialog


namespace Kwestiorariusz_ufoludka
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }



        private void ZapiszDoPlikuButton_Click(object sender, RoutedEventArgs e)
        {
            try
            {

                
                string documentsPath = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments);
                string fileName = "_MOJ_plik.txt";

                //string aDocumentsSubFolderPath = System.IO.Path.Combine(documentsPath, "aSubFodler");
                string downloadsPath = Environment.GetFolderPath(Environment.SpecialFolder.UserProfile) + "\\Downloads";
                string fullFilePath = System.IO.Path.Combine(downloadsPath, fileName);

                //ComboBox:
                string cBxText = ((ComboBoxItem)cBx.SelectedItem).Content.ToString();

                //RadioButton Porwanie
                string idRbtnContent = pobierzDaneZRadioButtonOPorwaniu();
               


                //CheckBox and Lable
                string checkBox = lblData.Content.ToString() + " " + chBx.IsChecked;


                //Slider
                string sliderValue = slider.Value.ToString();

                // DatePicker
                DateTime? selectedDate = dateAttack.SelectedDate;
                //string dateAttactString = selectedDate.Value.ToString();
                string dateAttactString = selectedDate.HasValue ? selectedDate.ToString() : "brak daty"; //.ToString("yyyy-MM-dd");
                
                //Password
                string psw = passwordBox.Password.ToString();


                string textToWrite = $"tekst: {tBx.Text} \nComboBox: {cBxText}" +
                    $"                 \nrRodzaj porwania: {idRbtnContent} " +
                    $"                 \ncheckBox: {checkBox}" +
                    $"                 \nSLider: {sliderValue}" +
                    $"                 \nData Ataku na Ziemię: {dateAttactString}" +
                    $"                 \ntajne hasło: {psw}";

                File.WriteAllText(fullFilePath, textToWrite);

                MessageBox.Show($"Dane zostały zapisane w {fullFilePath}");
            }
            catch (Exception ex)
            {
                MessageBox.Show($"Wystąpił błąd: {ex.Message}");
            }
           
        }

        private string pobierzDaneZRadioButtonOPorwaniu()
        {
            string wybranyElement = "Nie wybrano";
            if (rBtn1.IsChecked == true)
            {
                wybranyElement = rBtn1.Content.ToString();
            }
            else if (rBtn2.IsChecked == true)
            {
                wybranyElement = rBtn2.Content.ToString();
            }
            else if(rBtn3.IsChecked == true)
            {
                wybranyElement = rBtn3.Content.ToString();
            }
            return wybranyElement;
        }
    }
}


```


# cały kod z wyborem pliku

zapisywanie do pliku przez okno dialogowe
```c#
using Microsoft.Win32; // Dodaj odpowiednie using dla OpenFileDialog i SaveFileDialog

private void SaveButton_Click(object sender, RoutedEventArgs e)
{
    // Utwórz okno dialogowe do wyboru miejsca i nazwy pliku
    SaveFileDialog saveFileDialog = new SaveFileDialog();
    saveFileDialog.Filter = "Pliki tekstowe (*.txt)|*.txt";
    saveFileDialog.DefaultExt = "txt";
    saveFileDialog.Title = "Zapisz plik";

    // Wyświetl okno dialogowe
    bool? result = saveFileDialog.ShowDialog();

    // Jeśli użytkownik wybrał miejsce i nazwę pliku i kliknął "Zapisz"
    if (result == true)
    {
        // Pobierz ścieżkę do wybranego pliku
        string filePath = saveFileDialog.FileName;

        // Tutaj można pobrać dane, które chcesz zapisać do pliku
        // Na przykład:
        string dataToSave = "To jest przykładowy tekst do zapisania.";

        // Zapisz dane do wybranego pliku
        System.IO.File.WriteAllText(filePath, dataToSave);
    }
}


```

teraz cały wformularz z tym oknem dialogowym
```c#
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;
using static System.Net.Mime.MediaTypeNames;
using System.Xml.Linq;
using Microsoft.Win32; // Dodaj odpowiednie using dla OpenFileDialog i SaveFileDialog


namespace Kwestiorariusz_ufoludka
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }


        private void ZapiszDoPlikuButton_Click(object sender, RoutedEventArgs e)
        {
            // Utwórz okno dialogowe do wyboru miejsca i nazwy pliku
            SaveFileDialog saveFileDialog = new SaveFileDialog();
            saveFileDialog.Filter = "Pliki tekstowe (*.txt)|*.txt";
            saveFileDialog.DefaultExt = "txt";
            saveFileDialog.Title = "Zapisz plik";

            // Wyświetl okno dialogowe
            bool? result = saveFileDialog.ShowDialog();

            // Jeśli użytkownik wybrał miejsce i nazwę pliku i kliknął "Zapisz"
            if (result == true)
            {
                // Pobierz ścieżkę do wybranego pliku
                string filePath = saveFileDialog.FileName;

                // Tutaj można pobrać dane, które chcesz zapisać do pliku
                // Na przykład:
                string dataToSave = daneDoZapisu();
;

                // Zapisz dane do wybranego pliku
                System.IO.File.WriteAllText(filePath, dataToSave);
            }
        }

        private string daneDoZapisu()
        {
                string documentsPath = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments);
                string fileName = "_MOJ_plik.txt";

                //string aDocumentsSubFolderPath = System.IO.Path.Combine(documentsPath, "aSubFodler");
                string downloadsPath = Environment.GetFolderPath(Environment.SpecialFolder.UserProfile) + "\\Downloads";
                string fullFilePath = System.IO.Path.Combine(downloadsPath, fileName);

                //ComboBox:
                string cBxText = ((ComboBoxItem)cBx.SelectedItem).Content.ToString();

                //RadioButton Porwanie
                string idRbtnContent = pobierzDaneZRadioButtonOPorwaniu();
            
                //CheckBox and Lable
                string checkBox = lblData.Content.ToString() + " " + chBx.IsChecked;

                //Slider
                string sliderValue = slider.Value.ToString();

                // DatePicker
                DateTime? selectedDate = dateAttack.SelectedDate;
                //string dateAttactString = selectedDate.Value.ToString();
                string dateAttactString = selectedDate.HasValue ? selectedDate.ToString() : "nie wybrano daty"; //.ToString("yyyy-MM-dd");
                
                //Password
                string psw = passwordBox.Password.ToString();

                string textToWrite = $"tekst: {tBx.Text} \nComboBox: {cBxText}" +
                    $"                 \nrRodzaj porwania: {idRbtnContent} " +
                    $"                 \ncheckBox: {checkBox}" +
                    $"                 \nSLider: {sliderValue}" +
                    $"                 \nData Ataku na Ziemię: {dateAttactString}" +
                    $"                 \ntajne hasło: {psw}";

            return textToWrite;

        }

        private string pobierzDaneZRadioButtonOPorwaniu()
        {
            string wybranyElement = "Nie wybrano";
            if (rBtn1.IsChecked == true)
            {
                wybranyElement = rBtn1.Content.ToString();
            }
            else if (rBtn2.IsChecked == true)
            {
                wybranyElement = rBtn2.Content.ToString();
            }
            else if(rBtn3.IsChecked == true)
            {
                wybranyElement = rBtn3.Content.ToString();
            }
            return wybranyElement;
        }
    }
}


```




