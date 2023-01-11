[[_ 0 PyQt5 From A-Z]]
#gui #pyqt5 

---
[[#QLabel class]]
[[#QPushButton class]]
[[#QCheckbox]]
[[#QRadioButton]]
[[#QLineEdit]]
[[#SpinBox]]
[[#Date and Time]]
[[#ComboBox]]

-----

- Current state
	- `isEnable(),  isWindow(), isVisible(), isModa(), etc.`
- Positioning
	- `move(x,y), pos(), resize(w,h), size(), setGeometry(x,y,w,h)`
- Styling
	- `setFont(QFont), setStyleSHeet(str)`
- Tips
	- `setStatusTip(string), setToolTip(string)` 
- Visibility
	- `show(), hide(), setEnabled(bool)`

---------------------
# QLabel class
#qlabel

constructor: `QLabel(str, parent)`
methods:
- `setText(str)`
- `setNum(int or dbl)`
- `setPixmap(QPixmap)`


```python
import sys  
  
from PyQt5.QtGui import QFont, QPixmap  
from PyQt5.QtWidgets import QLabel, QPushButton, QApplication, QDialog  
  
  
class DlgMain(QDialog):  
    def __init__(self):  
        super().__init__()  
        self.setWindowTitle("My G UUUUIII")  
        self.resize(400, 400)  
  
        self.btn = QPushButton("Change label", self)  
        self.btn.move(40,40)  
        self.btn.resize(120,50)  
        self.btn.clicked.connect(self.evt_btn_clicked)  
  
        self.lbl = QLabel("Old Text", self)  
        self.lbl.resize(200,200)  
        self.lbl.move(40, 100)  
        font = QFont("Times New Roman", 11, 15, True)  
        self.lbl.setFont(font)  
  
    def evt_btn_clicked(self):  
        str = """  
            <h1 > Header</h1>            <ul>                <li style="color:red" >Red</li>                <li>Green</li>        """        # self.lbl.setText(str)  
        # self.lbl.setText("New one")        # self.lbl.repaint() # sometime use this method to refresh a widget  
        pxm = QPixmap("fotos/fanny-cat.jpg").scaled(100,150)  
        self.lbl.setPixmap(pxm)  
        self.lbl.repaint()  
  
  
  
if __name__ == "__main__":  
    app = QApplication(sys.argv)  
    dlgMain = DlgMain()  
    dlgMain.show()  
    sys.exit(app.exec_())
```

----
# QPushButton class

#qpushbutton

```python
# QPushButton inherits from QAbstratButton and that inherits from QWidget
# methods
#   setIcon(QIcon)
#   setText(str)
#   setAutoRepeat(bool), setAutoRepeatDelay(msec), setAutoRepeatInterval
# signals
#   clicked
# QPushButton(str, parent)
#   setFlat(bool), setDefault(bool)
import sys
from PyQt5.QtWidgets import *
from PyQt5.QtGui import QFont, QIcon, QPixmap

class DlgMain(QDialog):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("PushButton")
        self.resize(200,200)

        self.btn = QPushButton("Disable Label", self)
        self.btn.setIcon(QIcon(QPixmap("images/face-icon.png")))
        self.btn.move(40,40)
        self.btn.resize(120,50)
        self.btn.clicked.connect(self.evt_btn_clicked)

        self.lbl = QLabel("Sme text", self)
        self.lbl.move(30,100)
        self.lbl.resize(100,100)
        font = QFont("Times New Roman",  11,75,True)
        self.lbl.setFont(font)

    def evt_btn_clicked(self):
        if self.lbl.isEnabled():
            self.lbl.setDisabled(True)
            self.repaint()
            self.btn.setText("Enable label")
            self.btn.repaint()
        else:
            self.lbl.setDisabled(False)
            self.lbl.repaint()
            self.btn.setText("Disable label")
            self.btn.repaint()
  

if __name__ == "__main__":
    app = QApplication([])
    main = DlgMain()
    main.show()
    sys.exit(app.exec_())
```



---------
# QCheckbox
It inherits from QAbstractButton.

**methods**:
- `isChecked()`
- `setChecked(bool)`

**signals**
- `clicked(bool)`
- `toggled(bool)`

**constructor**
`QCheckBox(str, parent)`:
	- methods
		- `isTristate()  setCheckState(Qt.CheckState)`
	- signal
		- `stateChanged(int)`


```python
import sys
from PyQt5.QtWidgets import *
from PyQt5.QtGui import QFont

class DlgMain(QDialog):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("Checkbox")
        self.resize(200,200)

        self.chkEnable = QCheckBox("Enable", self)
        self.chkEnable.move(30,40)
        self.chkEnable.setChecked(True)
        # event/signal handler/slot
        self.chkEnable.toggled.connect(self.evt_handler)

        # three state checkbox
        self.chkThree = QCheckBox("Three State", self)
        self.chkThree.move(30,70)
        self.chkThree.setTristate(True)
         self.chkThree.stateChanged.connect(self.evt_three_handler) 

        self.lbl = QLabel("Some text", self)
        self.lbl.move(40,100)
        self.lbl.resize(100,100)
        font=QFont("Times New Roman", 15,75, True)
        self.lbl.setFont(font)

    def evt_handler(self, chkd):
        if chkd:
            self.lbl.setDisabled(False)
        else:
            self.lbl.setDisabled(True)

    def evt_three_handler(self, state):
        print(state)
        if state == 0:
            QMessageBox.information(self, "State", "UnChecked")
        elif state == 2:
            QMessageBox.information(self, "State", "Checked")
        else:
            QMessageBox.information(self, "State", "Partially checked")
  

if __name__=="__main__":
    app = QApplication(sys.argv)
    main=DlgMain()
    main.show()

    sys.exit(app.exec_())
```

--------
# QRadioButton
It inherits from QAbstractButton
**constructor** `QRadioButton(str, parent)`

**by defaul radio buttons are autoexclusive:**
- only one of the radio buttons in  a single parent widget can be checked
- checking one automatically unchecks the others

**more than one group of radio buttons**
- put them in two separate parent widgets
- use `QButtonGroup`
	- `addButton(QAbstractButton, id)`
	- `checkedButton()`
	- `checkedid()`
	- in a `QButtonGroup check boxes can be exclusive and radio buttons can be non-exclusive`

```python
import sys
from PyQt5.QtWidgets import *

class Main(QDialog):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("QRadioButton")

        self.lbl = QLabel("My ETYKIETA", self)
        self.lbl.setStyleSheet("color: red; font-size:15px")
        self.lbl.move(50,30)

        # font color Button Group
        self.btgColor = QButtonGroup()
        self.rbtRed = QRadioButton("Red", self)
        self.rbtRed.move(50,60)
        self.rbtRed.setChecked(True)
        self.rbtRed.clicked.connect(self.evt_rbt_clicked)
        self.btgColor.addButton(self.rbtRed)

        self.rbtBlue = QRadioButton("Blue", self)
        self.rbtBlue.move(50,90)
        self.rbtBlue.setChecked(True)
        self.rbtBlue.clicked.connect(self.evt_rbt_clicked)
        self.btgColor.addButton(self.rbtBlue)


        self.rbtGreen = QRadioButton("Green", self)
        self.rbtGreen.move(50,120)
        self.rbtGreen.setChecked(True)
        self.rbtGreen.clicked.connect(self.evt_rbt_clicked)
        self.btgColor.addButton(self.rbtGreen)


        # font size Button Group
        self.btgSize = QButtonGroup()
        self.rbtSmall = QRadioButton("Small Text", self)
        self.rbtSmall.move(50,150)
        self.btgSize.addButton(self.rbtSmall, 10) # the second arg is an ID
        self.rbtSmall.clicked.connect(self.evt_rbt_clicked)

        self.rbtMedium = QRadioButton("Medium Text", self)
        self.rbtMedium.setChecked(True)
        self.rbtMedium.move(50,180)
        self.btgSize.addButton(self.rbtMedium, 15)
        self.rbtMedium.clicked.connect(self.evt_rbt_clicked)

        self.rbtLarge = QRadioButton("Large Text", self)
        self.rbtLarge.move(50,210)
        self.btgSize.addButton(self.rbtLarge, 20)
        self.rbtLarge.clicked.connect(self.evt_rbt_clicked)
  

    def evt_rbt_clicked(self):
        # when use only one group:
        #   sender treturns the widget that actually sent this event that we're handling
        #   rbt = self.sender()
        #   print(rbt)
        #   ss = "color:"+rbt.text()
        #   print(ss)
        #   self.lbl.setStyleSheet(ss)


        clr = self.btgColor.checkedButton()
        size = self.btgSize.checkedId()
        ss = f"color: {clr.text()} ; font-size: {size}px"
        print(ss)
        self.lbl.setStyleSheet(ss)

if __name__ == "__main__":
    app = QApplication(sys.argv)
    main = Main()
    main.show()

    sys.exit(app.exec_())
```

----
# QLineEdit
`QLineEdit(parent)
`QLineEdit(str, parent)`
methods
- `text(), setText(), clear()`
- `setPlaceHolderText(str)`
- `setReadOnly(bool)`
- `setEchoMode(QLineEdit.Password)`
- `setAlignment(Qt.Alignment)`
- `setMaxLength(init)`

signals
- `textCHanged(str)`
- `textEdited(str)`
- `editingFinished()`

```python
import sys
from PyQt5.QtWidgets import *
from PyQt5.QtCore import Qt

class Main(QDialog):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("QLineEdit")
        self.ledTitle = QLineEdit(self.windowTitle(), self)
        self.ledTitle.setPlaceholderText("Enter a new dialog title")
        #self.ledTitle.setReadOnly(True)
        self.ledTitle.setEchoMode(QLineEdit.Password)
        self.ledTitle.setAlignment(Qt.AlignRight)
        self.ledTitle.move(50,50)
        self.btnChange = QPushButton("Update title", self)
        self.btnChange.move(50,80)
        self.btnChange.clicked.connect(self.evt_btn_clicked)
        self.ledTitle.textChanged.connect(self.evt_ledTitle_textChanged)
  

    def evt_btn_clicked(self):
        res = QMessageBox.question(self, "Line Edit",
                                         "Are you sure you want to change the window title to '" +
            self.ledTitle.text() + "'" )
        if res == QMessageBox.Yes:
            self.setWindowTitle(self.ledTitle.text())

    def evt_ledTitle_textChanged(self, title):
        self.setWindowTitle(title)

if __name__ == "__main__":
    app = QApplication(sys.argv)
    main = Main()
    main.show()
    sys.exit(app.exec_())
```

----
# SpinBox
`QAbstractSpinBox`
methods:
- `setReadOnly(bool), isReadOnly()`
- `setAlignment(Qt.Alignment)`
- `setWrapping(bool)`
- `text(), clear(), selectAll()`
- `stepUpd(), stepDown()`

signals
- `editingFinished()`

**QSpinBox** for int
**QDubleSpinBox** for double
methods:
- `setMinimum(int), setMaximum(int), setRange(min, max)`
- `setSingleStep(int)`
- `setPrefix(str), setSuffix(str)`
- `setValue(int), value()`

signals
- `textChange(str)`
- `valueChanged(int)`

for `QDoubleSpinBox`:
- `setDecimals(int)`
- 
```python
import sys
from PyQt5.QtWidgets import *

class Main(QDialog):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("Spin box")

        self.spbInt = QSpinBox(self)
        self.spbInt.move(100,50)
        self.spbInt.setWrapping(True) # 0->99 , 99->0
        self.spbInt.setRange(0, 10000)
        self.spbInt.setSingleStep(200)
        self.spbInt.setValue(1000)
        self.spbInt.valueChanged.connect(self.evt_spbInt_valChanged)
        self.spbInt.editingFinished.connect(self.evt_spbInt_editingFinished)
  

        self.spbDouble = QDoubleSpinBox(self)
        self.spbDouble.move(100,80)
        self.spbDouble.setDecimals(5)
        self.spbDouble.setSingleStep(0.01)
        self.spbDouble.setPrefix("Latitude: ")
        self.spbDouble.setSuffix(chr(176))
        self.spbDouble.setRange(-90, 90)
        self.spbDouble.valueChanged.connect(self.evt_spbDble)

    def evt_spbDble(self, val):
        print(self.spbDouble.text())
        print(self.spbDouble.value())
  

    def evt_spbInt_valChanged(self, val):
        print(val, val % 200)
        if (val % 200):
            self.spbInt.setStyleSheet("color:red")
        else:
            self.spbInt.setStyleSheet("color:black")

    def evt_spbInt_editingFinished(self):
        QMessageBox.critical(self, "Invalid number", "Invalid value entered \n\nMust be divisible by 200" )
        self.spbInt.setFocus()

if __name__ == "__main__":
    app = QApplication(sys.argv)
    main=Main()
    main.show()

    sys.exit(app.exec_())
```

---
# QDateTimeEdit
It inherits from QAbstractSpinBox
`QDateTimeEdit(QTime, parent), QDateTimeEdit(QDate, parent)`
`QDateTimeEdit(QDateTime, parent), QDateTimeEdit(parent)`
methods
- `setCalendarPopup(bool), setCalendarWidget(QCalendarWidget)`
- `date(), time(), dateTime()`
- `setDate(), setTime(0, setDateTime()` 
- `setMinimumDate(QDate), setMaximumDate(QDate), setDateRange(QDate, QDate)`
- `setDisplayFormat(str)`
signals:
- `dateChanged(QDate), dateTimeChanged(QDateTime), timeChanged(Qtime)`
- inherited by `QDateEdit, QTimeEdit`

```python
import sys
from PyQt5.QtWidgets import *
from PyQt5.QtCore import *

class Main(QDialog):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("Date and Time")
      
		self.dteDt = QDateTimeEdit(QDate().currentDate(), self)
        self.dteDt.setCalendarPopup(True)
        self.dteDt.move(50,50)

        self.dteTm = QDateTimeEdit(QTime().currentTime(), self)
        self.dteTm.move(50, 80)
  

        self.dteDtTm = QDateTimeEdit(QDateTime(QDate.currentDate(), QTime().currentTime()), self)
        self.dteDtTm.move(50, 110)

        self.btn = QPushButton("Elapsed Time", self)
        self.btn.move(50, 140)
        self.btn.clicked.connect(self.evt_btn_clicked)

    def evt_btn_clicked(self):
        seconds = QDateTime().currentDateTime().secsTo(self.dteDtTm.dateTime())
        QMessageBox.information(self, "Elasped Time", f"{seconds} seconds have ekasoed since {self.dteDtTm.dateTime()}")


if __name__ == "__main__":
    app = QApplication(sys.argv)
    main=Main()
    main.show()
    sys.exit(app.exec_())
```


-----
# ComboBox
constructor: `QComboBox(parent)`
methods:
- `addItem(QIcon, txt, obj)`, `insertItem(idx, QIcon, txt, obje)`, `insertSeperator(idx)`
- 

















