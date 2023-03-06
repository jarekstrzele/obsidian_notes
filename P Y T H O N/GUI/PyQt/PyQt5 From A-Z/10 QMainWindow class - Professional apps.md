[[_ 0 PyQt5 From A-Z]]

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






