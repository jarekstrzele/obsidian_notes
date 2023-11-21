#wpf #game 

```xml
 ResizeMode="NoResize"
 Title="MainWindow" Height="600" Width="600">
```
na twardo ustawiony rozmiar okna bez możliwości zmiany rozmiaru

```c#
using System;
using System.Collections.Generic;
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

namespace TicTacToe
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {   
        private bool IsPlayerTurn { get; set; }
        private int Counter { get; set; }
        private Button[] btns = new Button[9];
        public MainWindow()
        {
            InitializeComponent();
            InitializeBtnArray();
            NewGame();
        }

        public void NewGame()
        {
            IsPlayerTurn = true; //pierwszy gracz to krzyżyk
            Counter = 0;
            ClearBtnArray();

        }

        private void Button_Click(object sender, RoutedEventArgs e)
        {
            // Słowo kluczowe var w języku C# jest używane do deklarowania zmiennych lokalnych,
            // których typ jest określany przez kompilator na podstawie przypisanej wartości.
            // Oznacza to, że kompilator analizuje przypisaną wartość
            // i dedukuje odpowiedni typ zmiennej.
            Counter++;
            if (Counter >= 9)
            {
                MessageBox.Show("Koniec gry", "Koniec", MessageBoxButton.OK);
                NewGame();
                return;
            }

            if (isWinner())
            {
                MessageBox.Show("Koniec gry", $"Wygrał {999}", MessageBoxButton.OK);
            }

            var button = sender as Button;
            button.FontSize = 30;
            button.Background = Brushes.Red;
            // button.Content = "X";
            button.Content = IsPlayerTurn ? "O" : "X";
            button.Background = IsPlayerTurn ? Brushes.BlueViolet : Brushes.Bisque;

            IsPlayerTurn ^= true;


        }

        private void InitializeBtnArray()
        {
            for (int i = 0; i < btns.Length; i++)
            {
                btns[i] = FindName($"btn{i + 1}") as Button;
                btns[i].Background = Brushes.Tan;
            }
        }

        private void ClearBtnArray()
        {
            for (int i = 0; i < btns.Length; i++)
            {
                btns[i].Content = string.Empty;
                btns[i].Background = Brushes.Tan;
            }
        }
        private bool isWinner()
        {
            if (areRowsTheSame()) return true;

            return false;
        }
        private bool areRowsTheSame()
        {
            for (int i = 0; i < 9; i += 3 )
            {
                if (!isRowEmpty(i))
                {
                    return areThreeTheSame(i);
                }
            }

            return false;
        }
        private bool isRowEmpty(int row)
        {
            if (btns[row].Content == string.Empty || btns[row + 1].Content == string.Empty ||
                    btns[row + 2].Content == string.Empty)
                {
                    return false;
                }
            
            return true;
        }
        private bool areThreeTheSame(int row)
        {
            for (int i = 0;i < 3;i++) {
                if (btns[row].Content == btns[row+1].Content && btns[row].Content == btns[row + 2])
                {
                    return true;
                }
            }
            return false;
        }
    }
}

```












