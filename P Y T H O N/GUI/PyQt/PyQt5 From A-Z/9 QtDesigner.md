[[_ 0 PyQt5 From A-Z]]

QtDesinger
https://build-system.fman.io/qt-designer-download

**Qt Designer is pure Qt**
- it doesn't know ANYTHING about Python
- it does allow you to visually design your interface
- it also allows you to connect pre-defined signals to predefined slots
- custom slots must be written and connected after-the-fact in Python
- Saves the user interface as an xml file that must be convert to python

**workflow**
1. defign interface
2. connect signals to slots (pre-defined slots only)
3. save
4. compile to python
5. write custom slots in python 
6. test
7. modyfy interface (return to 3.)

## `ctr+r` -> Preview

## Edit > Edit Tab order


# Slots, Signals
- Find *Signals, Slots Editor* (View)
- add sender, signal, receiver, slot (ctr+r -> you can see)

OR
- Edit> *Edit Signals, Slots*
- attach by mouse widgets that you want to connect




-------
# From QtDesigner to Python
QtDesigner produces a xml file.

### `pyuic5`
- command line utility
- converts `.ui` file to a python file
	- `.ui` file is `XML` file saved from
	- `pyuic fileui.ui -o file.py`
	- you can made executable with `-x` flag
		- `pyuic -x flieui.ui -o file.py` -> executable python module
		- 
When you install `pyqt5`, you also install `pyuic5`

------------
# Addinng custom slots and other QtDesigner modification

> 
> `toggled` event is sending a boolean value!!!!
> 



