[[_ 0 PyQt5 From A-Z]]


- `setStyleSheet(str)` - QApplication, QWidget
- similar to CSS
```css
selector{
	property1:val1;
	property2:val2;
}
```

**selector**s
- class name - apply to all elements in a class
- `className#variableName` - apply to a specific instance of class
- `className:state` - apply to a specific state
- `className::subcontrol` - apply to specific sub-controls, up-arrow, etc.
- `className[property=value]` apply to all elements that satisfy the property condition
- `classname1 classname2` apply to all elements fo classname2 that are children of classname1
- `classnam1, classnam2` - apply to both classname 1 and classname2
- 

**properties**
- `color` - text color: red,
- `background-color`
- `background-image: url(:urlfotos/bear.jpg`
- `border:width style color`
	- `border: 2px dashed rgb(255,0,0)`
- `border-radius: 5px`
- `font: bold italic large "Times New Roman"`
- `height: 10px`
- `width:20px`
- `lineedit-password-character: 9679`
- `margin, padding`
	- `Qt Box Model` (margin(border(*padding*(**content**)*padding*)border)margin)
- `text-align`


Style Sheet
## https://doc.qt.io/qt-5/stylesheet-reference.html


## Qt Style sheets in practice 
something doesn't work
```python
import sys
from PyQt5.QtWidgets import *

class Main(QDialog):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("First Style Sheet")
        # for all container
        # self.setStyleSheet("background-color:red; border-radius: 3px; padding: 3px")

        sStyle="""
            QPushButton {
                background-color:blue;
                color: white ;
                border-radius: 3px;
                padding: 3px;
            }

            QPushButton {
                background-color: red;
                color:white;
                border-radius: 3px;
                padding: 3px;
            }

            QPushButton: hover {
                background-color:green;
                color: white ;
                border-radius: 3px;
                border: 5px solid #000000;
                padding: 3px;
            }

        """
  

        self.setStyleSheet(sStyle)
        self.btn1 = QPushButton("Button 1")
        self.btn1.setDefault(True)
        self.btn2 = QPushButton("Button 2")
        self.btn3 = QPushButton("Button 3")
        self.btn3.setStyleSheet("background-color:orange; border-radius: 3px; border: 2 solid #000000; padding: 3px")
        # self.btn3.setDefault(True)

        self.lytMain = QVBoxLayout()
        self.lytMain.addWidget(self.btn1)
        self.lytMain.addWidget(self.btn2)
        self.lytMain.addWidget(self.btn3)

        self.setLayout(self.lytMain)


if __name__ == "__main__":
    app = QApplication([])
    main=Main()
    main.show()

    sys.exit(app.exec_())
```










