#wpf/layout

[[_ C Sharp od Podstaw do WPF i XAML]]


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















