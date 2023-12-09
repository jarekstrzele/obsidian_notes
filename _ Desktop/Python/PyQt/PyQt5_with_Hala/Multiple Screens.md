https://www.youtube.com/watch?v=82v2ZR-g6wYi
#pyqt5  #hala  #youtube 

```python
import sys
from PyQt5.uic import loadUi
from PyQt5 import QtWidgets
from PyQt5.QtWidgets import QDialog, QApplication,QMainWindow

class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        loadUi("ui_modules/myscreen_1.ui", self)
        self.button.clicked.connect(self.gottoScreen2)

    def gottoScreen2(self):
        widget.setCurrentIndex(widget.currentIndex()+1)
 

class Screen2(QDialog):
    def __init__(self):
        super().__init__()
        loadUi("ui_modules/myscreen_2.ui", self)
        self.setWindowTitle("Screen 2")
        self.pushButton.clicked.connect(self.gotoscreen1)

    def gotoscreen1(self):
        widget.setCurrentIndex(widget.currentIndex()-1)
  

# main
app = QApplication([])
# QStackWidget is a series of widgets or a series of QDialogs or a list of QDialogs
widget = QtWidgets.QStackedWidget()
mainWin=MainWindow()
screen2=Screen2()
widget.addWidget(mainWin)
widget.addWidget(screen2)
widget.setFixedHeight(300)
widget.setFixedWidth(400)
widget.setWindowTitle("Multiple Screen")
widget.show()

try:

    sys.exit(app.exec_())

except:

    print("Exiting")
```

other version 

```python
class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        loadUi("ui_modules/myscreen_1.ui", self)
        self.button.clicked.connect(self.gottoScreen2)

  

    def gottoScreen2(self):
        screen2=Screen2()
        widget.addWidget(screen2)
        widget.setCurrentIndex(widget.currentIndex()+1)

  

class Screen2(QDialog):
    def __init__(self):
        super().__init__()
        loadUi("ui_modules/myscreen_2.ui", self)
        self.setWindowTitle("Screen 2")
        self.pushButton.clicked.connect(self.gotoscreen1)

  

    def gotoscreen1(self):
        mainWin=MainWindow()
        widget.addWidget(mainWin)
        widget.setCurrentIndex(widget.currentIndex()+1)
```



