`TextBlock`, `Button`

zapisywanie do pliku
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







