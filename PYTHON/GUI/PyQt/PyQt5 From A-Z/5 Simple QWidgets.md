[[_ 0 PyQt5 From A-Z]]
#gui #pyqt5 

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






















