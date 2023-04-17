#qtdesigner  

https://www.youtube.com/watch?v=xL2NdSubiNY

`Table Widget`

```python
import sys
from PyQt5.uic import loadUi
from PyQt5 import QtWidgets
from PyQt5.QtWidgets import QDialog, QApplication

  
class Main(QDialog):
    def __init__(self):
        super().__init__()
        loadUi("ui_modules/myTableWidget.ui", self)
        self.tableWidget.setColumnWidth(0,250)
        self.tableWidget.setColumnWidth(1,100)
        self.tableWidget.setColumnWidth(2,350)
        
        self.load_data()

    def load_data(self):
        people=[
            {"name":"John", "age":45,"address":"New York"}
            , {"name":"Jerry", "age":75,"address":"Olsztyn"}
            , {"name":"Zosia", "age":43,"address":"Kraków"}
            , {"name":"Kasia", "age":15,"address":"Paryż"}
        ]
  
        row = 0
        self.tableWidget.setRowCount(len(people))
        for person in people:
            self.tableWidget.setItem(row, 0, QtWidgets.QTableWidgetItem(person["name"]))
            self.tableWidget.setItem(row, 1, QtWidgets.QTableWidgetItem(str(person["age"])))
            self.tableWidget.setItem(row, 2, QtWidgets.QTableWidgetItem(person["address"]))
            row += 1
  

app = QApplication([])
main=Main()
  

main.show()
try:
    sys.exit(app.exec_())
except:
    print("Exiting")
```

----
https://www.youtube.com/watch?v=xL2NdSubiNY&list=PLs3IFJPw3G9KhF7BeGOItwoKKLD8e3Dwu&index=2








