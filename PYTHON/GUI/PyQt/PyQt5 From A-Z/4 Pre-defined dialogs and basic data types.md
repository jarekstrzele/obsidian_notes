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



