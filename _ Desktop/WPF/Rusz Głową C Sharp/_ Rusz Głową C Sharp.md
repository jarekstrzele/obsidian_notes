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
<TextBlock Grid.Column="0" HorizontalAlignment="Center" Grid.Row="0" TextWrapping="Wrap" Text="?" VerticalAlignment="Center" FontSize="36" MouseDown="TextBlock_MouseDown"/>
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
```c#
List<string> animalEmoji = new List<string>()
```



















