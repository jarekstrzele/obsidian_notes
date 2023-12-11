[[_ 0 PyQt5 From A-Z]]

absolute positioning: `.move(x,y)`

## Layouts:
- QLayout - abstract class
	- addWidget(), removeWidget(), count(), setAlignment(), setEnabled(bool)
	- **QBoxLayout**:
		- `QVBocLoyout()`
		- `QHBoxLaout()`
		- addLayout(lyt, int), addStretch(init), setDirection()
	- **QFormLayout()**
		- addRow(lbl, QWidgets), insertRow(idx, lbl, QWidget), removeRow(idx)
		- setLabelAlignment(Qt.QAlignment)
	- **QGridLayout()**
		- addWidget(QWiget, x, y, xspan, yspan)

---
# QBoxLayout
```python
import sys
from PyQt5.QtWidgets import *

class Main(QDialog):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("First Layout")

        ## widgets
        self.lbl1 = QLabel("FIrst lable")
        self.btn2 = QPushButton("BTN 2")
        self.led3 = QLineEdit("Line Edit 3")
        self.cmb4 = QComboBox()
        self.cmb4.addItems(["utem 1", "item2", "item 3"])

        ## layout
        # self.mainLayout = QHBoxLayout()
        self.mainLayout = QVBoxLayout()
        self.mainLayout.addStretch() # strech from the left
        self.mainLayout.addWidget(self.lbl1)
        self.mainLayout.addWidget(self.btn2)
        self.mainLayout.addStretch() # strech in the middle
        self.mainLayout.addWidget(self.led3)
        self.mainLayout.addWidget(self.cmb4)
        self.mainLayout.addStretch() # strech from the right

        self.setLayout(self.mainLayout)

if __name__ == "__main__":
```

```python
        ## layout
        self.mainLayout = QHBoxLayout()
        #self.mainLayout = QVBoxLayout()
        # .addWidget(object, number_that_indicates_how_many_place_takes_that_widget)
        self.mainLayout.addWidget(self.lbl1, 20)
        self.mainLayout.addWidget(self.btn2, 10)
        self.mainLayout.addWidget(self.led3, 10)
        self.mainLayout.addWidget(self.cmb4, 20)
        self.mainLayout.addStretch(4)

        self.setLayout(self.mainLayout)
```



----
# QFormLayout
```python
import sys
from PyQt5.QtWidgets import *
from PyQt5.QtCore import *

class Main(QDialog):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("First FORMLayout")
        
        # widgets
        self.ledFname = QLineEdit("Joe")
        self.ledLname = QLineEdit("SMith")
        self.dteStarted = QDateTimeEdit()
        self.spbAge = QSpinBox()
        self.btnSubmit = QPushButton("Submit")

        ## layout
        self.mainLayout = QFormLayout()
        self.mainLayout.setLabelAlignment(Qt.AlignRight) #doesn't work
        self.mainLayout.setRowWrapPolicy(QFormLayout.WrapLongRows) # doesn't work
        self.mainLayout.addRow("First Name: ", self.ledFname)
        self.mainLayout.addRow("Last Name: ", self.ledLname)
        self.mainLayout.addRow("Date starte", self.dteStarted)
        self.mainLayout.addRow("Age: ", self.spbAge)
        self.mainLayout.addRow("", self.btnSubmit)

        self.setLayout(self.mainLayout)
```

----
# QGridLayout
```python
import sys
from PyQt5.QtWidgets import *

class Main(QDialog):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("QGrid")

        # widgeets
        self.btn0 = QPushButton("0")
        self.btn1 = QPushButton("1")
        self.btn2 = QPushButton("2")
        self.btn3 = QPushButton("3")
        self.btn4 = QPushButton("4")
        self.btn5 = QPushButton("5")
        self.btn6 = QPushButton("6")
        self.btn7 = QPushButton("7")
        self.btn8 = QPushButton("8")
        self.btn9 = QPushButton("9")

        self.btn_calc = QPushButton("Calculate")
        
        self.setupLayout()

    def setupLayout(self):
        # layout
        self.mainLayout = QGridLayout()
        #              .addWidget(object, row, column, spanrow, spancol)
        self.mainLayout.addWidget(self.btn1, 4, 0)
        self.mainLayout.addWidget(self.btn2, 4, 1)
        self.mainLayout.addWidget(self.btn3, 4, 2)
        self.mainLayout.addWidget(self.btn4, 3, 0)
        self.mainLayout.addWidget(self.btn5, 3, 1)
        self.mainLayout.addWidget(self.btn6, 3, 2)
        self.mainLayout.addWidget(self.btn7, 2, 0)
        self.mainLayout.addWidget(self.btn8, 2, 1)
        self.mainLayout.addWidget(self.btn9, 2, 2)
        self.mainLayout.addWidget(self.btn0, 5, 1)
        self.mainLayout.addWidget(self.btn_calc, 0,0, 1, 3)

        self.setLayout(self.mainLayout)
  

if __name__ == "__main__":
    app =QApplication(sys.argv)
    main=Main()
    main.show()

    sys.exit(app.exec_())
```


--------
# Compound Layouts
to combine a bunch of different types of layouts

Project:
- top level QVBoxLayout
	- QLabel
	- QHBoxLaout
		- QListBox - 45%
		- QVboxLayout - 10%
			- 2 x QPushButtons
		- QListBox 45%
	- QHBoxLayout
		- 2 x QFormLayout 55%, 45%
	- QHBoxLayout
		- 3 QFormLayouts
	- QHBoxLayout
		- 2 x QPushBottons
		- strech to the left



---
# QStackedLayout

## LAYOUTS:
### Absolute positioning
	- lots of work
	- not elastic
### Layouts
#### QLayouts - abstract class:
- QBoxLayout
- QFormLayout
- QGridLayout
- QStackedLayout
	- achieve similar functionality to a tabbed form but use QComboBox ot QListBox ot QRadioButtons to select layout
	- `addWidget(), setCurrentIndex(idx)`
	can contain several diffeten widgets, but only one of them will be visible at a time and will decide which one is visible at a time by electing it from  a Combobox


```python
import sys
from PyQt5.QtWidgets import *
from PyQt5.QtGui import *
from PyQt5.QtCore import QDate

class Main(QDialog):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("QGrid")

        # create widgets
        self.cmbSelector = QComboBox()
        self.cmbSelector.addItems(["General", "Species", "Location", "Surveys"])
        self.cmbSelector.currentIndexChanged.connect(self.evt_cmbSelector_changed)
        self.wdgGeneral = QWidget()
        self.wdgSpecies = QWidget()
        self.wdgLocation = QWidget()
        self.wdgSurveys = QWidget()

        ## general widgets
        self.lblNestID = QLabel("34")
        self.dteFound = QDateTimeEdit(QDate(2016, 5, 13))
        self.dteLast = QDateTimeEdit(QDate(2020,4,14))
        self.chkActive = QCheckBox()

        ## species widgets
        self.cmbSpecies = QComboBox()
        self.cmbSpecies.addItem("Red-tailed Hawk", 800)
        self.cmbSpecies.addItem("Swainsons Hawk", 400)
        self.cmbSpecies.addItem("Other", 1600)

        self.ledSpecies = QLineEdit()
        self.spbBuffer = QSpinBox()
        self.spbBuffer.setValue(800)


        # location Widgets
        self.spbLatitude = QDoubleSpinBox()
        self.spbLongitute = QDoubleSpinBox()

        # survey widget
        self.lstSurveys = QListWidget()
        self.lstSurveys.addItem("03/24/2020 - MSM - INACTIVE")
        self.lstSurveys.addItem("03/30/2020 - MSM - INACTIVE")
        self.lstSurveys.addItem("04/07/2020 - MSM - INACTIVE")
        self.lstSurveys.addItem("04/14/2020 - MSM - ACTIVE!!")
        self.btnAddSurvey = QPushButton("Add Survey")


        # layouts
        self.setup_layouts()

    def setup_layouts(self):
        self.lyt_main = QHBoxLayout()
        self.lyt_left = QVBoxLayout()
        self.lyt_right = QStackedLayout()

        self.lyt_main.addLayout(self.lyt_left)
        self.lyt_main.addLayout(self.lyt_right)

        self.lyt_left.addWidget(self.cmbSelector)
        self.lyt_left.addStretch()

        # add stacked widgets to  rightlayout
        self.lyt_right.addWidget(self.wdgGeneral)
        self.lyt_right.addWidget(self.wdgSpecies)
        self.lyt_right.addWidget(self.wdgLocation)
        self.lyt_right.addWidget(self.wdgSurveys)

        ### setup general widget

        self.lyt_general = QFormLayout()
        self.lyt_general.addRow("Nest ID:", self.lblNestID )
        self.lyt_general.addRow("Date FOund: ", self.dteFound)
        self.lyt_general.addRow("Date Last Surveyed: ", self.dteLast)
        self.lyt_general.addRow("Currently Active", self.chkActive)
        self.wdgGeneral.setLayout(self.lyt_general)

        # setup location widget
        self.lyt_location = QFormLayout()
        self.lyt_location.addRow("Latitute:", self.spbLatitude)
        self.lyt_location.addRow("Longitude:", self.spbLongitute)
        self.wdgLocation.setLayout(self.lyt_location)

        # setup species widget
        self.lyt_species = QFormLayout()
        self.lyt_species.addRow("Species: ", self.cmbSpecies)
        self.lyt_species.addRow("Species: ", self.ledSpecies)
        self.lyt_species.addRow("Buffer: ", self.spbBuffer)
        self.spbBuffer.setSuffix(" m")
        self.wdgSpecies.setLayout(self.lyt_species)

        # setup surveys widget
        self.lyt_surveys = QVBoxLayout()
        self.lyt_surveys.addWidget(self.lstSurveys)
        self.lyt_surveys.addWidget(self.btnAddSurvey)
        self.wdgSurveys.setLayout(self.lyt_surveys)

        self.setLayout(self.lyt_main)

    def evt_cmbSelector_changed(self, idx):
        self.lyt_right.setCurrentIndex(idx)

if __name__ == "__main__":
    app =QApplication(sys.argv)
    main=Main()
    main.show()

    sys.exit(app.exec_())
```







