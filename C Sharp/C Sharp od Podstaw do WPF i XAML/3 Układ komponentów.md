#wpf/layout

[[_ C Sharp od Podstaw do WPF i XAML]]

**Layouts** są responsywne


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
## Attached Properties
`Grid.Row` oraz `Grid.Column` to są *Attached Properties* dołączone właściwości, bo tak naprawdę zostały dodane do `Rectangle` i `TextBlock` przez `Grid`, wewnątrz którego one są

`<RowDefinition Height="250"/>` ustawia na "twardo" wysokość wiersza a resza jest dopasowywana automatycznie

==`<RowDefinition Height="Auto"/>` wysokość wiersza dopasowuje do elementów, które w nim występują
jeżeli element występujący w środku nie ma zdefiniowanej wysokości, to zostanie "skasowany"==


## Margin, Padding, Span
elementy wewnątrz `Grid` mają `Margin`, `Padding`

Rozpinanie na więcej niż jedną kolumnę `Grid.ColumnSpan="<number>"`
```xml
<Button Grid.Row="3" Grid.ColumnSpan="2"/>

<Rectangle Grid.Row="2"  Grid.Column="3" Fill="Blue"   Margin="20,5,10,5" />

<Button Grid.Row="3" Grid.ColumnSpan="2" Padding="5"  Margin="10,10,10,10" FontSize="36" >Kilknij</Button>
```

## Można mieć jeden `Grid` w drugim.
```xml
<Grid>
    <Grid.RowDefinitions >
        <RowDefinition />
        <RowDefinition />
        <RowDefinition/>
        <RowDefinition/>
    </Grid.RowDefinitions >
    <Grid.ColumnDefinitions>
        <ColumnDefinition/>
        <ColumnDefinition/>
        <ColumnDefinition/>
        
    </Grid.ColumnDefinitions>
    
    <Grid Grid.Column="1">
        <Grid.RowDefinitions >
            <RowDefinition />
            <RowDefinition />
            <RowDefinition/>
            <RowDefinition/>
        </Grid.RowDefinitions >
        <Grid.ColumnDefinitions>
            <ColumnDefinition/>
            <ColumnDefinition/>
            <ColumnDefinition/>

        </Grid.ColumnDefinitions>
        <Rectangle Fill="PaleGoldenrod" />
        <Rectangle Grid.Column="2" Grid.Row="1" Fill="YellowGreen" />
    </Grid>
    <Rectangle Grid.Row="2"  Grid.Column="3" Fill="Blue"   Margin="20,5,10,5" />
    <Rectangle Fill="DarkMagenta" />
    <TextBlock Grid.Row="1" Grid.Column="1" FontSize="72" HorizontalAlignment="Center" VerticalAlignment="Center" FontWeight="Bold"  >X</TextBlock>
    <Button Grid.Row="3" Grid.ColumnSpan="2" Padding="5"  Margin="10,10,10,10" FontSize="36" >Kilknij</Button>

</Grid>
```

-------
# Grid Splitter (rozdzielacz)


## rozkład proporcjonalny
```xml
 <Grid>
     <Grid.ColumnDefinitions>
         <ColumnDefinition Width="1*"/>
         <ColumnDefinition Width="3*"/>
     </Grid.ColumnDefinitions>

     <TextBlock Margin="10,10,10,10" FontSize="38" >Menu</TextBlock>
     <TextBlock Grid.Column="1" 
                Margin="10,10,10,10" 
                FontSize="28" 
                TextWrapping="Wrap">Lorem ipsumLorem ipsumLorem ipsumLorem ipsum</TextBlock>
  
 </Grid>
```

```
<ColumnDefinition Width="1*"/>
<ColumnDefinition Width="3*"/>
```
podział proporcjonalny, czyli druga kolumna ma być trzy razy większa niż pierwsza

## splitter pionowy
Dodać do `xaml` >`<Gird>` > ` <GridSplitter Width="3" Background="DarkCyan" />` (`Width` jest konieczny, z automoatu w row=0, clomun=0)

```xml
<GridSplitter Grid.Column="1" Width="3" Background="DarkCyan" HorizontalAlignment="Left" />
       
```


## splitter poziomy
zmieniamy cały `Grid`
```xml
<Grid>
    <Grid.RowDefinitions>
         <RowDefinition Height="1*" MinHeight="80" MaxHeight="120"/>
        <RowDefinition Height="3*"/>
    </Grid.RowDefinitions>

    <TextBlock Margin="10,10,10,10" FontSize="38" >Menu</TextBlock>
    <TextBlock Grid.Row="1" 
               Margin="10,10,10,10" 
               FontSize="28" 
               TextWrapping="Wrap">Lorem ipsumLorem ipsumLorem ipsumLorem ipsum</TextBlock>
    <GridSplitter Height="3" Background="Crimson" VerticalAlignment="Bottom" HorizontalAlignment="Stretch" />

</Grid>
```

` <RowDefinition Height="1*" MinHeight="80" MaxHeight="120"/>` ustawianie maksymalnej i minimalne wysokości dla danego wiersza!!!


# `<UniformGrid>`
Domyślnie wszystkie elementy będą miały tyle samo miejsca
(wpisuj `Button` po kolei, aby zobaczyć, jak zmienia się układ)
```xml
 <UniformGrid>
     <Button> 1 </Button>
     <Button> 2</Button>
     <Button> 3</Button>
     <Button> 4</Button>
     <Button> 5</Button>
 </UniformGrid>
```

## zmiana domyślnych zachowań `UniformGrid`

```xml
<UniformGrid Columns="3">
    <Button Margin="10,10,10,10" FontSize="48" FontWeight="Bold" FontFamily="Bookman Old Style"> 1 </Button>
    <Button Margin="10,10,10,10" FontSize="48" FontWeight="Bold" FontFamily="Bookman Old Style"> 2</Button>
    <Button Margin="10,10,10,10" FontSize="48" FontWeight="Bold" FontFamily="Bookman Old Style"> 3</Button>
    <Button Margin="10,10,10,10" FontSize="48" FontWeight="Bold" FontFamily="Bookman Old Style"> 4</Button>
    <Button Margin="10,10,10,10" FontSize="48" FontWeight="Bold" FontFamily="Bookman Old Style"> 5</Button>
    <Button Margin="10,10,10,10" FontSize="48" FontWeight="Bold" FontFamily="Bookman Old Style"> 6</Button>
    <Button Margin="10,10,10,10" FontSize="48" FontWeight="Bold" FontFamily="Bookman Old Style"> 7</Button>
    <Button Margin="10,10,10,10" FontSize="48" FontWeight="Bold" FontFamily="Bookman Old Style"> 8</Button>
    <Button Margin="10,10,10,10" FontSize="48" FontWeight="Bold" FontFamily="Bookman Old Style"> 9</Button>
</UniformGrid>
    
```

`<UniformGrid Columns="3">` ustalamy, że maksymalnie mogą być trzy kolumy (inne ustawienia też są możliwe)


# `<StackPanel>`
jak `UniformGrid` jednokolumnowy lub jednowierszowy

## poziomy
```xml
    <StackPanel>
        <Button Width="50" Height="100">1</Button>
        <Button Width="150" Height="50" HorizontalAlignment="Left">2</Button>
        <Button>3</Button>
        <Button>4</Button>
    </StackPanel>
```

## pionowy
```xml
  <StackPanel Orientation="Horizontal">
      <Button>1</Button>
      <Button Width="300" Background="Beige">2</Button>
      <Button VerticalAlignment="Top" Width="200">3qdwqdqdq</Button>
      <Button>4</Button>
  </StackPanel>
```


## `<WrapPanel>`
Jak `StackPanel`, ale zawija elementy (np. wyświetlanie zdjęć)

`<WrapPanel Orientation="Vertical">`
`<WrapPanel Orientation="Horizontal">`


# DockPanel
#sharp/wfp/dock_panel
ważna jest kolejność ustawiania elementów
` <DockPanel LastChildFill="True">` wartość "True" jest domyślna

```xml
 <DockPanel LastChildFill="True">
     <Button DockPanel.Dock="Top">Menu górne </Button>
     <Button DockPanel.Dock="Bottom">Footer</Button>

     <Button DockPanel.Dock="Left" Width="100">Left </Button>
     <Button DockPanel.Dock="Right">Right </Button>
     <Button>Center</Button>
     <!-- a to jest komentarz 
             wielo linniowy
     -->
 </DockPanel>
```


# Canvas
używamy, gdy wiemy, o stałym położeniu elementu `x,y`
`<Canvas>` ustawia elementy relatywnie, samo jest relatywne do swojego rodzica, czyli `<Window>` (lub innego tagu)

napisz ten kod raz z `Grid` a raz bez
```xml
<Grid Width="250">
 <Canvas>
  <Button Content="Button" Canvas.Left="400" Canvas.Top="114" HorizontalAlignment="Center" Height="30" VerticalAlignment="Top" Width="80"/>
  <Button Content="Button" Canvas.Left="400" Canvas.Top="144" Height="30" Width="80" HorizontalAlignment="Center" VerticalAlignment="Top"/>
  <Button Content="Button" Canvas.Left="400" Canvas.Top="174" Height="30" Width="80"/>

 </Canvas>   
</Grid>
```


# ScrollViewer
np. gdy chcemy zawijać tekst, który wychodzi poza okienko
```xml
  <Grid >
      <TextBlock TextWrapping="Wrap">fwoeij fwioefw[eofiw[eoif feow[if [woeimewofm[weofm wemf[woefim fmfwoeifj  efmweoifweoifwmeofimweoifm
      </TextBlock>
  </Grid>
```

lub używamy scroll
```xml
  <Grid >
      <ScrollViewer VerticalScrollBarVisibility="Auto" HorizontalScrollBarVisibility="Auto">
          <TextBlock >fwoeij fwioefw[eofiw[eoif feow[if [woeimewofm[weofm wemf[woefim fmfwoeifj  efmweoifweoifwmeofimweoifm
          </TextBlock>
      </ScrollViewer>
  </Grid>
```







