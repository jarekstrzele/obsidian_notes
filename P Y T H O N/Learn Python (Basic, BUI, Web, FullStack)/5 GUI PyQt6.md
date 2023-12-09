#pyqt6 #qt 


# Qt
- it is used foe develeping graphical user interface (destop, mobile)

# PyQt6
a set of python bindins for building  cross-platfrom apps

*PyCharm*
## `pip install pyqt6`


```python
import sys  
from PyQt6.QtWidgets import QApplication, QWidget  
# QApplication control flow, an object of that class is a singleton  
  
  
app = QApplication(sys.argv)  
window = QWidget()  
window.show()  
  
  
sys.exit(app.exec())
```



# QMainWindow
`QMainWindow` class provides a main application window
It has its own layout to which you can add QToolBars, QDockWigets, QMenuBar, QStatusBar



