>[!info]
>Stack widget allows us to do is to have multiple bits of content on screen but only showing  one thing at a time

```python
# This Python file uses the following encoding: utf-8
import sys

from PySide6.QtWidgets import QApplication, QMainWindow

# Important:
# You need to run the following command to generate the ui_form.py file
#     pyside6-uic form.ui -o ui_form.py, or
#     pyside2-uic form.ui -o ui_form.py
from ui_form import Ui_MainWindow

class MainWindow(QMainWindow):
    def __init__(self, parent=None):
        super().__init__(parent)
        self.ui = Ui_MainWindow()
        self.ui.setupUi(self)

        self.ui.stackedWidget.setCurrentWidget(self.ui.home)

        self.ui.btn_blue.clicked.connect(self.showBlue)
        self.ui.btn_red.clicked.connect(self.showRed)
        self.ui.btn_yellow.clicked.connect(self.showYellow)

    def showBlue(self):
        self.ui.stackedWidget.setCurrentWidget(self.ui.blue)

    def showRed(self):
        self.ui.stackedWidget.setCurrentWidget(self.ui.red)

    def showYellow(self):
        self.ui.stackedWidget.setCurrentWidget(self.ui.yellow)


if __name__ == "__main__":
    app = QApplication(sys.argv)
    widget = MainWindow()
    widget.show()
    sys.exit(app.exec())

```

