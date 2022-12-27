[[_ 0 PyQt5 From A-Z]]


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











