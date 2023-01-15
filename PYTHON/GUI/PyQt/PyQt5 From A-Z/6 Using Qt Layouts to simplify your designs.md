[[_ 0 PyQt5 From A-Z]]

absolute positioning: `.move(x,y)`

## Layouts:
- QLayout - abstract class
	- addWidget(), removeWidget(), count(), setAlignment(), setEnabled(bool)
	- **QBoxLaout**:
		- `QVBocLoyout()`
		- `QHBoxLaout()`
		- addLayout(lyt, int), addStretch(init), setDirection()
	- **QFormLaout()**
		- addRow(lbl, QWidgets), insertRow(idx, lbl, QWidget), removeRow(idx)
		- setLabelAlignment(Qt.QAlignment)
	- **QGridLaout()**
		- addWidget(QWiget, x, y, xspan, yspan)



# QFormLaoyt
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





