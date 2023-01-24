[[_ 0 PyQt5 From A-Z]]

QtDesinger
https://build-system.fman.io/qt-designer-download

**Qt Designer is pure Qt**
- id doesn't know ANYTHING about Python
- it does allow you to visually design your interface
- it also allows you to connect pre-defined signals to predefined slots
- custom slots must be written and connected after-the-fact in Python
- Saves the user interface as an xml file that must be convert to python

**workflow**
1. defign interface
2. connect signals to slots (pre-defined slots only)
3. save
4. compule to python
5. write cystom slots in python t
6. test
7. modyfy interface (return to 3.)






