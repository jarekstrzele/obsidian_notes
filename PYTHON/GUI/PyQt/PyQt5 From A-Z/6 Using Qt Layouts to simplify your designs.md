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
















