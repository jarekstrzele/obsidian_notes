#csharp

[[_ C Sharp]]

# gra memo ze zwierzakami

>[!info] interfehs WPF
>Interfejs użytkownika aplikacji WPF jest zbudowany z
>-  kontrolek (przycisków, etykiet, pól wyboru itd.). 
>- **Siatka** jest kontenerem, czyli kontrolką specjalnego rodzaju, która może zawierać inne kontrolki. Siatka pozwala użyć wierszy i kolumn do zdefiniowania układu okna.


## TextBlock
*WPF* używa kontrolek *TextBlock* do wyświetlania tekstu. My użyjemy ich do wyświetlania dopasowywanych zwierząt.

W kodzie *XAML* tej kontrolki *TextBlock* jest pięć właściwości:
- `Text` określa tekst wyświetlany w oknie.
- `HorizontalAlignment` wyrównuje tekst do lewej, do prawej lub względem środka.
- `VerticalAlignment` wyrównuje tekst względem góry, środka lub dołu.
- `Margin` ustawia margines względem krawędzi kontenera.
- `TextWrapping` określa, czy tekst w kontrolce ma być zawijany.


## GUI
```xml
        Title="MainWindow" Height="450" Width="800">
<Grid x:Name="mainGrid" >
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition />
            <ColumnDefinition />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
        </Grid.RowDefinitions>

<TextBlock Grid.Column="1" HorizontalAlignment="Center" Grid.Row="1" TextWrapping="Wrap" Text="?" VerticalAlignment="Center" FontSize="36"/>
<TextBlock Grid.Column="0" HorizontalAlignment="Center" Grid.Row="0" TextWrapping="Wrap" Text="?" VerticalAlignment="Center" FontSize="36"/>
        <TextBlock Grid.Column="1" HorizontalAlignment="Center" 
           Grid.Row="0" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>
        <TextBlock Grid.Column="2" HorizontalAlignment="Center" 
           Grid.Row="0" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>
        <TextBlock Grid.Column="3" HorizontalAlignment="Center" 
           Grid.Row="0" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>
        <TextBlock Grid.Column="0" HorizontalAlignment="Center" 
           Grid.Row="1" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>
        <TextBlock Grid.Column="2" HorizontalAlignment="Center" 
           Grid.Row="1" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>
        <TextBlock Grid.Column="3" HorizontalAlignment="Center" 
           Grid.Row="1" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>
        <TextBlock Grid.Column="0" HorizontalAlignment="Center" 
           Grid.Row="2" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>
        <TextBlock Grid.Column="1" HorizontalAlignment="Center" 
           Grid.Row="2" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>
        <TextBlock Grid.Column="2" HorizontalAlignment="Center" 
           Grid.Row="2" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>
        <TextBlock Grid.Column="3" HorizontalAlignment="Center" 
           Grid.Row="2" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>
        <TextBlock Grid.Column="0" HorizontalAlignment="Center" 
           Grid.Row="3" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>
        <TextBlock Grid.Column="1" HorizontalAlignment="Center" 
           Grid.Row="3" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>
        <TextBlock Grid.Column="2" HorizontalAlignment="Center" 
           Grid.Row="3" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>
        <TextBlock Grid.Column="3" HorizontalAlignment="Center" 
           Grid.Row="3" TextWrapping="Wrap" Text="?" VerticalAlignment="Center"
           FontSize="36"/>

    </Grid>
</Window>

```


## Logika
dodanie emoji przez klawisz `Windows i .` Emoji umieść w cudzysłowach
```c#
List<string> animalEmoji = new List<string>(){

    "🐸","🐸",
    "🙊","🙊",
    "🐷","🐷",
    "👽","👽",
    "🐭","🐭",
    "🐔","🐔",
    "🐘","🐘",
    "🐳","🐳"
};     

```
dodaj emoji do `TextBlock`s
```c#
Random random = new Random();
foreach(TextBlock textblock in mainGrid.Children.OfType<TextBlock>())
{
    int index = random.Next(animalEmoji.Count);
    string nextEmoji = animalEmoji[index];
    textblock.Text = nextEmoji;
    animalEmoji.RemoveAt(index);
}
```
**wyjaśnienie**
Ten fragment kodu wykonuje iterację przez wszystkie elementy `TextBlock` znajdujące się w kolekcji `Children` kontrolki `mainGrid` i aktualizuje ich tekst losowym emoji zwierzęcia. Aby to zrobić, korzysta z kilku kluczowych elementów:

1. **Obiekt `Random`:**
    
    - `Random random = new Random();` tworzy nową instancję klasy `Random`, która służy do generowania liczb pseudolosowych.
2. **Pętla `foreach`:**
    
    - `foreach(TextBlock textblock in mainGrid.Children.OfType<TextBlock>())` iteruje przez wszystkie elementy w `mainGrid.Children`, które są typu `TextBlock`. `mainGrid.Children` zawiera wszystkie elementy potomne kontrolki `mainGrid`, a metoda `.OfType<TextBlock>()` filtruje te elementy, zwracając tylko te, które są typu `TextBlock`.
3. **Losowanie i aktualizacja tekstu:**
    
    - W ciele pętli, `int index = random.Next(animalEmoji.Count);` losuje indeks z zakresu od 0 do liczby elementów w liście `animalEmoji` (nie włączając wartości maksymalnej, czyli `Count`).
    - `string nextEmoji = animalEmoji[index];` pobiera emoji zwierzęcia znajdujące się na wylosowanym indeksie z listy `animalEmoji`.
    - `textblock.Text = nextEmoji;` aktualizuje właściwość `Text` aktualnie przetwarzanego `TextBlock` wylosowanym emoji.
4. **Usuwanie użytego emoji:**
    
    - `animalEmoji.RemoveAt(index);` usuwa emoji, które zostało przypisane do `TextBlock`, z listy `animalEmoji`. Zapobiega to ponownemu użyciu tego samego emoji w innym `TextBlock` w ramach tego samego procesu losowania i aktualizacji.


## git
>Git jest otwartym systemem kontroli wersji. Istnieje wiele niezależnych serwisów takich jak GitHub, które udostępniają usługi związane z systemem Git (na przykład przestrzeń dyskową na kod i dostęp do repozytorium z poziomu internetu).

Więcej o systemie Git dowiesz się na stronie https://git-scm.com.


## dodanie kliknięcia myszą
- kliknij w `xaml` znacznik `<TextBlock>` po prawej stronie będzie we właściwościach ikonka błyskawicy - kliknij ją,

> **Procedura obsługi zdarzeń** jest metodą wywoływaną przez aplikację po zajściu określonych zdarzeń.
> Takie **zdarzenia to**
> - wciśnięcie klawisza, 
> - przeciągnięcie elementu, 
> - zmiana wielkości okna lub, naturalnie, 
> - ruchy i kliknięcia myszą.

- znajdź zdarzenie `MouseDown` 
- do pola obok wpisz *TextBlock_MouseDown* i kliknij dwa razy  --> do wybranego wcześniej `TextBlock` zostanie metoda









