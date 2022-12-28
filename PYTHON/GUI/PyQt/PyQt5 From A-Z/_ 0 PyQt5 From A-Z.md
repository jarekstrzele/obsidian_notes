#python #gui #pyqt5

# https://doc.qt.io


- PyQt began in 1998 by Riverbank computing
- SIP is technology developed by Riverbank to create python binings
- SIP is open source and has been used in other projects
- PyQt uses GPL license
- PySIde is another set of python bindings for Qt using SIP



```shell

$ python3 -m venv ./venv
$ source venv/bin/activate
(venv) $ pip install pyqt5 pyqt5-tools
```

Windows: `venv\Scripts\activate`, `venv/Scripts/activate`

==Qt==
- framework for creating graphical user interfaces
- platfrom independent
- was written in C, QtCreator ID
	- SIP creates python bindings for C++ (Qt) classes
- QtDesigner Visual interace design
- Pyuic5, PyQt5
- signals and slots
- 


## Graphical User Interfaces
- command line driven procedural programs were the norm for decades
	- limited user interaction
- Graphical User Interaces
	- Xerox Alto 1973
	- Apple McIntosh 1984
	- Windows 3.1 1991
- How do you program a GUI
	- Visual Basic
	- Ob ject oriented
	- Event - driven programs

### Qt Framework
- Qt is a GUI framework for app development
	- cross platform
	- multi-language
		- python bindings
		- java, javascript, go rust, haskell, ...
	- commercial or open-source licensing
	- in addition to GUI tools
		- SQL
		- Multimedia
		- Bluetooth
		- Network
		- Multithreading
	- includes IDE - Qt Creator
		- for python: development is Qt Designer
			- use it to build the UI
			- sace it as a `ui` file
			- use `pyuic5` to convert the `ui` file to a python file
			- write the event handlers in python
			- ==events== in Qt are called ==signals==
			- ==event handlers== are called ==slots==
			- all QtWidget have predefined signals that they emit
			- you can also create your own custom signals

>[!important] (PyQt)
>`app = QApplication([])`
>This is a requirement of Qt: Every GUI app must have exactly one instance of `QApplication`.
>`[]` represent the command line args passed to the application


>[!note] QWigets
>Every thing you see in a (Py)Qt app is a widget
>Widgets can be nested
>some widgets: `QLabel`



## First program -procedal approche
```python
import sys   
from PyQt5.QtWidgets import *  
  
app = QApplication(sys.argv)  
dlgMain = QDialog() # a container for all widgets that will be added
#  dlgMain     = QMainWindow()
#  dlgMain      = QWidget()
dlgMain.setWindowTitle("My GUI")  
dlgMain.show() # show the GUI  
  
sys.exit(app.exec_()) # execute the app



```

```python
import sys  
from PyQt5.QtWidgets import *  
  
class DlgMain(QDialog):  
    def __init__(self):  
        super().__init__()  
        self.setWindowTitle("My Gui")  
  
if __name__ == "__main__":  
    app = QApplication(sys.argv)  
    dlgMain = DlgMain()  
    dlgMain.show()  
    sys.exit(app.exec_())
```

## Second program - OOP
```python
import sys  
from PyQt5.QtWidgets import *  
  
  
class DlgMain(QDialog):  
    def __init__(self):  
        super().__init__()  
        self.setWindowTitle("My GUI")  
        self.resize(200,200)  
  
        self.ledText = QLineEdit("my GUI", self)  
        self.ledText.move(50, 50)  
  
        self.btnUpDate = QPushButton("Update Window Title", self)  
        self.btnUpDate.move(50, 80)  
        self.btnUpDate.clicked.connect(self.evt_btnUpDate_clicked)  
  
    def evt_btnUpDate_clicked(self):  
        self.setWindowTitle(self.ledText.text())  
  
  
if __name__ == "__main__":  
    app = QApplication(sys.argv)  #create app
    dlgMain = DlgMain()  # create main GUI canvas
    dlgMain.show()  # show the GUI
    sys.exit(app.exec_()) # execute the app
		



```


## Signals and Slots

### signals
analohous to events
`obj.signal.connect(self.method)`
old syntax `self.connect(obj, SIGNAL("signal"), self.method))`

to define yourown siglnals:
`signal  = pyqt5Signal(*args)`
`signal.emit(*args)`
old syntax: `self.emit(SIGNAL("signal"), *args)`

### slots
analogous to event handlers









