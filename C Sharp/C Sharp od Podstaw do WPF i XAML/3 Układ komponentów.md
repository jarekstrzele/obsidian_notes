#wpf/layout

[[_ C Sharp od Podstaw do WPF i XAML]]

**Layo
# `<Grid>` siatka
na początku jest jeden wiersz jedna kolumna
lewy górny róg to `row=0, column=0`

```xml
   <Grid>
       <Grid.RowDefinitions >
           <RowDefinition/>
           <RowDefinition/>
           <RowDefinition/>
       </Grid.RowDefinitions >
       <Grid.ColumnDefinitions>
           <ColumnDefinition/>
           <ColumnDefinition/>
           <ColumnDefinition/>
           
       </Grid.ColumnDefinitions>
       <Rectangle Fill="Blue" />
   </Grid>    
```
prostokąt będzie w lewym górnym rogu
domyślnie siatka dzielona jest proporcjonalnie


```xml
  ...
   <RowDefinition Height="250"/>
   <RowDefinition Height="Auto"/>
   ....
  
  <Rectangle Grid.Row="2"  Grid.Column="3" Fill="Blue" />
  <Rectangle Fill="DarkMagenta" />
  <TextBlock Grid.Row="1" Grid.Column="1" FontSize="72" HorizontalAlignment="Center" VerticalAlignment="Center" FontWeight="Bold"  >X</TextBlock>
    
```
`Grid.Row` oraz `Grid.Column` to są *Attached Properties* dołączone właściwości, bo tak naprawdę zostały dodane do `Rectangle` i `TextBlock` przez `Grid`, wewnątrz którego one są

`<RowDefinition Height="250"/>` ustawia na "twardo" wysokość wiersza a resza jest dopasowywana automatycznie

==`<RowDefinition Height="Auto"/>` wysokość wiersza dopasowuje do elementów, które w nim występują
jeżeli element występujący w środku nie ma zdefiniowanej wysokości, to zostanie "skasowany"==

elementy wewnątrz `Grid` mają `Margin`, `Padding`

Rozpinanie na więcej niż jedną kolumnę `Grid.ColumnSpan="<number>"`
```xml
        <Button Grid.Row="3" Grid.ColumnSpan="2"/>

```
















