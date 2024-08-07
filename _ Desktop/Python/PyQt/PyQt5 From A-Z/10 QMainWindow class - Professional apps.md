[[_ 0 PyQt5 From A-Z]]

[[#QMenu]]
[[#QToolbar]]
[[#QStatusBar]]
[[#QSplitter]]
[[#QSplitter]]
[[#Mutli-dialog applications]]


---
# QMenu
- only availble with `QMainWindow`
- can be created manually but mucj easier in QtDesigner
- can be nested serval lebels deep
- every menu items is a `QAction`
	- similat to a QPushButton but the same QAction can be triggered with a menu shortcu ot toolbar icon
	- QActions emi a trigger signal when triggered
	- 

in QtDesigner > project > MainWindow
	- you get MainWIndow with tree widgets:
		- centralWidget
		- meubar
		- statusbar(a place to show msgs for users)

`pyuic5 file.ui -0 pythonfile.py`

```python
import sys
from PyQt5.QtWidgets import *
from ui_modules.menu import *


class MainMenu(QMainWindow, Ui_MainWindow):
    def __init__(self):
        super().__init__()
        self.setupUi(self)
 

if __name__ == "__main__":
    app = QApplication([])
    mainMenu = MainMenu()
    mainMenu.show()
 

    sys.exit(app.exec_())
```


# QToolbar
- also only available in QMainWIndow
- can be dockable
- toolbar is composed of QActions
- toobar is dockable

in QtDesigner > that project with QMainWindow and Menu > right click and select `add toolbar` > see *Action Editor*

```python
import sys
from PyQt5.QtWidgets import *
from ui_modules.menu import *

class MainMenu(QMainWindow, Ui_MainWindow):
    def __init__(self):
        super().__init__()
        self.setupUi(self)
		    self.actionOpen.triggered.connect(self.evt_open_triggered)
        self.actionQuit.triggered.connect(self.evt_quit_triggered)


    def evt_quit_triggered(self):
        sys.exit(0)    
 

    def evt_open_triggered(self):
        sFile, sFilter = QFileDialog.getOpenFileName(self, "Open", "ui/", "User interface files (*.ui)")
        if sFile:
            print(sFile)
        else:
            print("Canceld by user")
  

if __name__ == "__main__":
    app = QApplication([])
    mainMenu = MainMenu()
    mainMenu.show()
    sys.exit(app.exec_())
```


--------
# QStatusBar
#qstatusbar
- only availble in QMainWindow
- provides feedback to user
- methods
	- showMessage(txt, msec)
	- clearMessage()
	- addWidget(QWidget)
	- addPermanentWidget(QWidget)

You work on the same project menu.ui
```python
class MainMenu(QMainWindow, Ui_MainWindow):
    def __init__(self):
        super().__init__()
        self.setupUi(self)
    self.actionOpen.triggered.connect(self.evt_open_triggered)
     self.actionQuit.triggered.connect(self.evt_quit_triggered)
        self.btnDisplay.clicked.connect(self.evt_btnDisplay_clicked)


        self.btn=QPushButton("Push Memee")
        self.statusbar.addPermanentWidget(self.btn)
        self.prg = QProgressBar()
        self.prg.setValue(43)
        self.prg.setStyle(QStyleFactory.create("Window"))
        # self.statusbar.addWidget(self.prg)
        self.statusbar.addPermanentWidget(self.prg)


    def evt_btnDisplay_clicked(self):
        self.statusbar.showMessage(self.ledMsg.text(), self.spbMsec.value())

    def evt_quit_triggered(self):
        sys.exit(0)    
  
    def evt_open_triggered(self):
        sFile, sFilter = QFileDialog.getOpenFileName(self, "Open", "ui/", "User interface files (*.ui)")
        if sFile:
            print(sFile)
        else:
            print("Canceld by user")
```



---------
# QSplitter
#qsplitter
- container that is user adjustable
- methods:
	- addWidget(QWidget)
	-  insertWidget(idx, QWidget)
	-  setOrentation(Qt.orientationQWidget)
	-  setHandleWidth(int)
- signals
	- splitterMoved(pos, idx)
	- 

you work on the same project

```python
import sys, os
from PyQt5.QtWidgets import *
from ui_modules.menu import *

class MainMenu(QMainWindow, Ui_MainWindow):
    def __init__(self):
        super().__init__()
        self.setupUi(self)
       self.actionOpen.triggered.connect(self.evt_open_triggered)
        self.actionQuit.triggered.connect(self.evt_quit_triggered)

        self.prg = QProgressBar()
        self.prg.setValue(43)
        self.prg.setStyle(QStyleFactory.create("Window"))
        # self.statusbar.addWidget(self.prg)
        self.statusbar.addPermanentWidget(self.prg)
        self.listWidget.addItems(os.listdir("ui_modules/"))
        self.listWidget.itemDoubleClicked.connect(self.evt_lst_dbl)


    def evt_lst_dbl(self, lwi):
        # QMessageBox.information(self, "File", f"you selected {lwi.text()}")
        try:
            f = open("ui_modules/"+lwi.text())
            self.plainTextEdit.setPlainText(f.read())
        except PermissionError:
            self.statusbar.showMessage("I can't open that file", 2500)
 

    def evt_quit_triggered(self):
        sys.exit(0)    
  
    def evt_open_triggered(self):
        sFile, sFilter = QFileDialog.getOpenFileName(self, "Open", "ui/", "Any file (*.*)")
        if sFile:
            f = open(sFile)
            self.plainTextEdit.setPlainText(f.read())
        else:
            print("Canceld by user")


if __name__ == "__main__":
    app = QApplication([])
    mainMenu = MainMenu()
    mainMenu.show()

    sys.exit(app.exec_())
```

------------
# Mutli-dialog applications
- import the class from the file where it was defined
- three methods
	- **method 1**
		- `from treeWidget import DlgMain`
		- `dlgTrw = DlgMain()`
	- **method 2**
		- `import treeWidget`
		- `dlgTrw = treeWidget.DlgMain()`
	- **method 3**
		- `import treeWidget as tw`
		- `dlgTrw = tw.DlgMain()`
- then show and execute (start the event loop) the dialog
	- `dlgTrw.show()`
	- `dlgTrw.exec_()`
	- 
 
```python
from PyQt5.QtWidgets import *
from ui_modules.menu import *
import exe_to_my_clacul # to jest plik z wcześniej napisaną aplikacją kalkulatora

  
  

class MainMenu(QMainWindow, Ui_MainWindow):
    def __init__(self):
        super().__init__()
        self.setupUi(self)
       self.actionOpen.triggered.connect(self.evt_open_triggered)
        self.actionQuit.triggered.connect(self.evt_quit_triggered)

        self.actionAbout_menu.triggered.connect(self.evt_help_triggered) # do menu Help podłączam metodę, która włączy nowe okno

    def evt_help_triggered(self):
		# tworzę nowy obiekt klasy, która jest w zaimportowanym pliku z kalkulatorem
        mycal= exe_to_my_clacul.Main()
		# pokazuję to okno
        mycal.show()
		# utrzymuję okno w istnieniu
        mycal.exec_()
```

----
# to make widgets streching when window changes its size

```python
class MainMenu(QMainWindow, Ui_MainWindow):
    def __init__(self):
        super().__init__()
        self.setupUi(self)

		# make a layout
        self.lyt_main = QHBoxLayout()
		# set layout for centralwidget od MainWindow
        self.centralwidget.setLayout(self.lyt_main)
		# add plitter to that laoyt
		self.lyt_main.addWidget(self.splitter)
```










