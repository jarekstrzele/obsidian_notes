[[_ 0 PyQt5 From A-Z]]

----
[[#QMessageBox]]
[[#QInputDialog]]
[[#Choosing a File wit QFileDialog]]
[[#Colors in Qt]]
[[#QFonts and the QFontDialog]]
[[#Data and time handler]]
[[#Images in Qt]]


----
# QMessageBox
- provide output to user
- can be used for simple input queries (yes/no)
- method 1 - **static methods**
	- parent (*the container that the widget your are creating is going to go into it*) = QWidget that you want the message bo to be centered in 
	- `result = QMessageBox.warning(parent, "Title of Box", Message")`
		- information
		- warning
		- critical
		- question

	- `result = QMessageBox.warning(parent, "Title of Box", Message", btn1 | btn2 | btn3 , btnDefault)`
		- QMessageBox.Cancel, 
		- QMessageBox.OK,
		- QMessageBox.Yes,
		- QMessageBox.No., ... 
- method 2 - **QMessageBox**
	- `msgDiskFull = QMessageBox()`
	- `msgDiskFull.setText("You hard drive is almpst full")
	- `msgDiskFull.setDetailedText("Please make some ....")` 
	- `msgDiskFull.setIcon(QMessageBox.Information)` 
	- `msgDiskFull.setWindowTitle("Full Drive")` 
	-  `msgDiskFull.SetStandardButtons(QMessageBox.Ok | QMessagebox.Cancel )` 
	- `msgDiskFull.exec_()` 

```python
import sys  
from PyQt5.QtWidgets import *  
  
class Main(QDialog):  
    def __init__(self):  
        super().__init__()  
        self.resize(200,200)  
        self.setWindowTitle("my G u I")  
  
        self.btn = QPushButton("show Message", self)  
        self.btn.move(40, 40)  
        self.btn.clicked.connect(self.evt_btn_clicked)  
  
    def evt_btn_clicked(self):  
        res = QMessageBox.question(self, "Disk Full", "your disk drive is almost full")  
        # res = QMessageBox.critical(self, "Disk Full", "your disk drive is almost full")  
        # res = QMessageBox.information(self, "Disk Full", "your disk drive is almost full")        # print(res)  
        if res == QMessageBox.Yes:  
            QMessageBox.information(self, "", "You clicked YES")  
  
        else:  
            QMessageBox.information(self, "Title No", "You clicked No!!!!")  
  
if __name__=="__main__":  
    app = QApplication(sys.argv)  
    main = Main()  
    main.show()  
    sys.exit(app.exec_())
```


# QInputDialog
QInputDiolog:
- parent = dialog that the InputDialog will be centered in
- `QInputDialog.getText(parent, "Title", "Prompt", text="Default")`
- `QInputDialog.getInt(parent, "Title", "Prompt", iDef, iMin, iMax, iStep)`
- `QInputDialog.getDouble(parent, "Title", "Prompt", dDef, dMin, dMax, dDigits)`
- `sList=["it1", "it2", ]` 
- `QInputDialog.getItem(parent, "Title", "Promp", sList, editable=False)` 

res = QInputDialog.getText(prent, ....) -> (val, status)

```python
import sys  
from PyQt5.QtWidgets import *  
  
  
class DlgMain(QDialog):  
    def __init__(self):  
        super().__init__()  
        self.setWindowTitle("My Gui")  
        self.resize(200,200)  
  
        self.btn=QPushButton("Show Input", self)  
        self.btn.move(40,40)  
        self.btn.clicked.connect(self.evt_btn_clicked)  
  
    def evt_btn_clicked(self):  
        # res = QInputDialog.getText(self, "Text", "Enter your name:")  
        # print(res)        
        sName, bOk = QInputDialog.getText(self, "Text", "Enter your name:")  
        if bOk:  
            QMessageBox.information(self, "Name", "Your name is " + sName)  
        else:  
            QMessageBox.critical(self, "Canceled", "User canceled")  
  
  
if __name__ == "__main__":  
    app = QApplication([])  
    dlgMain = DlgMain()  
    dlgMain.show()  
    sys.exit(app.exec_())
```


`iAge, bOk = QInputDialog.getInt(self, "Text", "Enter your age:", 22, 18, 65, 1)`

```python
lstColor = ['Red', 'Green', 'Blue']  
iAge, bOk = QInputDialog.getItem(self, "Text", "Enter your favorite color:", lstColor, editable=False)
```


---
# Choosing a File wit QFileDialog

QFileDialog class:
- uses the operating systems file dialogs to open or save a filename
- `QFileDialog.getOpenFIleName(parent, "Title", directory, types)`
	- directory is a string
	- types is a string
		- *"Shape files (\*.shp )"*
- `QFileDialog.getSaveFileDialog(parent, "Title", dir, types)`
	- you can add a name that doesn't exist
- `QFileDialog.getOpenFileNames(parent, "Title", Directory, types)`
	- can select multiple files
	- return values is an array of filenames

```python
  
class DlgMain(QDialog):  
    def __init__(self):  
        super().__init__()  
        self.setWindowTitle("My Gui")  
        self.resize(200,200)  
  
        self.btn=QPushButton("Open File", self)  
        self.btn.move(40,40)  
        self.btn.clicked.connect(self.evt_btn_clicked)  
  
    def evt_btn_clicked(self):  
        res = QFileDialog.getOpenFileName(self, "Open File", "C:\\Users\\jarek\\Prog", "JPG File (*.jpg);; PNG Files(*.png);; All files (*.*)")  
        print(res)
```

---
# Colors in Qt
**QColor object** 
```python
color = QColor(255, 0, 0)  # czerwony
color = QColor('blue')  # niebieski
color = QColor('#2df1c3')
color = QColor(255,0,0,125) # przeźroczystość
color = QColor()
	- setRed(100), setGreen(219), etc.
color = QColor.fromRgb(255, 255, 0)  # żółty
```

User can choose the color:
```python
color = QColorDialog.getColor(QColor, parent, "Title")
```


```python
import sys  
  
from PyQt5.QtGui import QColor  
from PyQt5.QtWidgets import *  
  
  
class DlgMain(QDialog):  
    def __init__(self):  
        super().__init__()  
        self.setWindowTitle("My Gui")  
        self.resize(200,200)  
        self.btn=QPushButton("Choose color", self)  
        self.btn.move(40,40)  
        self.btn.clicked.connect(self.evt_btn_clicked)  
  
    def evt_btn_clicked(self):  
        color = QColorDialog.getColor(QColor("#FF0000"), self, "Choose Color")  
        print(color.value())  
    
if __name__ == "__main__":  
    app = QApplication([])  
    dlgMain = DlgMain()  
    dlgMain.show()  
    sys.exit(app.exec_())
```

----
# QFonts and the QFontDialog
**QFont object**
- `QFont("Arial", 24)` 
- QFont(type, height, weight, italic) -> `QFont("Arial", 24, 81, true)`
- `QFont()`
	- setFamily(), setWeight(), setPointSize(), ...
- `font, bOk = QFontDialog.getFont()`

```python
from PyQt5.QtWidgets import QFontDialog, QLabel

font, ok = QFontDialog.getFont()
if ok:
    label = QLabel('Wybrana czcionka: {}'.format(font.family()))
    label.setFont(font)
    label.show()
```

```python
class DlgMain(QDialog):  
    def __init__(self):  
        super().__init__()  
        self.setWindowTitle("My Gui")  
        self.resize(200,200)  
  
        self.btn=QPushButton("Choose font", self)  
  
        self.btn.move(40,40)  
        self.btn.clicked.connect(self.evt_btn_clicked)  
  
    def evt_btn_clicked(self):  
        font, ok = QFontDialog.getFont()  
        print(font, ok)
```


```python
import sys  
  
from PyQt5.QtGui import QColor, QFont  
from PyQt5.QtWidgets import *  
  
  
class DlgMain(QDialog):  
    def __init__(self):  
        super().__init__()  
        self.setWindowTitle("My Gui")  
        self.resize(200,200)  
  
        self.btn=QPushButton("Choose font", self)  
        font = QFont("Times New Roman", 20, 75, True)  
        self.btn.setFont(font)  
        self.btn.move(40, 40)  
        self.btn.clicked.connect(self.evt_btn_clicked)  
  
    def evt_btn_clicked(self):  
        font, ok = QFontDialog.getFont()  
        if ok:  
            print(font.family())  
            print(font.italic())  
            print(font.bold())  
            print(font.weight())  
            print(font.pointSize())  
            self.btn.setFont(font)  
  
if __name__ == "__main__":  
    app = QApplication([])  
    dlgMain = DlgMain()  
    dlgMain.show()  
    sys.exit(app.exec_())
```


---
# Data and time handler 

==Dates in Qt(QtCore)==
- QDate object
	- `QDate(YYYY, MM, DD)`
	- `addDays(), addMonths(), toJulianDay(), dayOfWeek(), dayOfYear(), daysTo(QDate)`
- Qtime object
	- `QTime(HH, MM, SS, ms)`
	- `addSeconds(). swcsTo(QTime), toString()`
- QTimeZone object
	- `QTimeZone(seconds)`
- QDateTime object
	- `QDateTime(QDate, QTime)`
	- `QDateTime(QDate, QTime, QTimeZone)`
	- `addSecs(), toString(). toSecsSinceEpoch(), secsTo(), daysTo()`


```python
import sys  
  
from PyQt5.QtCore import QDate, QTime, QDateTime  
from PyQt5.QtGui import QColor, QFont  
from PyQt5.QtWidgets import *  
  
  
class DlgMain(QDialog):  
    def __init__(self):  
        super().__init__()  
        self.resize(200,200)  
  
        self.btn = QPushButton("Dates", self)  
        self.btn.move(40, 40)  
        self.btn.resize(120, 50)  
        self.btn.clicked.connect(self.evt_btn_clicked)  
  
    def evt_btn_clicked(self):  
        dt = QDate.currentDate()  
        print(dt.toString())  
        print(dt.toJulianDay())  
        print(dt.dayOfYear())  
        print(dt.dayOfWeek())  
        print(dt.addDays(23).toString())  
        tm = QTime(14,30,15)  
        print(tm.toString())  
        tm2 = QTime(20,15)  
        print(tm2)  
        print(tm2.toString())  
        print(tm.secsTo(tm2))  
        dtm = QDateTime.currentDateTime()  
        print(dtm.toString())  
  
if __name__ == "__main__":  
   app = QApplication(sys.argv)  
   dlgMain = DlgMain()  
   dlgMain.show()  
   sys.exit(app.exec_())
```



--------
# Images in Qt
==QPixmap(w,h)==:
	- fill(QColor), load(file)

==QPixmap(file)==

`size(), height(), width(), scaled(w,h)`

`scaledToWidth(w), scaledToHeight(h)`

`save(file)`

Other classes
`QImage, QPicture, QBitmap, QPainter`



---------
#

















