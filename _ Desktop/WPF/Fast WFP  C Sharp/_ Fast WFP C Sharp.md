#csharp  #udemy  #sharp/wfp


# WPF structure and project files
`Solution` / `Rozwiązanie` - is like a container or a folder for holding one or more projects inside it

`App.xaml` it is the starting point of the application and you can easily change the default or start-up window

The `xaml` file is for saving the design of my form 

`MainWIndow.xaml` user interface

`MainWindow.xaml.cs` all of the logics and codes or user generated codes are inside this file

--------
## Window
WINDOW -- you can change: size, colour, border, icon, cursor, title, isEnable, Visibility

`WindowStartUpLocation` :`CenterScreen`

## Properties in XAML
```xml
<Window 
	BorderBrush=""
> 
<!--- ....
-->

```

`WindowStyle` {None,  SingleBorderWindow, ... }

### resize mode `ResizeMode=`
`noResize`
`CanMinimize`
`CanResize`
`CanResizewithGrid`

### font
If you change font options in `Window`, it effects all elements inside that `Window`


### `WindowState`
for controlling the maximize and minimize a state of  the window
- `normal`
- `minimize`
- `miximize`

### `Topmost`
the window always will be on the top


### `Taskbar`
`SHowInTaskbar`

### RTL & LTR
`Flow Direction`: LeftToRight or  RightToLeft languages


### Width and Height
min, max















