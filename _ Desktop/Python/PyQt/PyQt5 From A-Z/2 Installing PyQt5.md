#pyqt5 
- python 3.7 (`python3 --version`)
- PyCharm
- PyQt5
- QtDesigner
	- pyuic5
	- pyrrc5


## setting up your envirenment on Windows

PyCharm:
- File > Settings > NameOfProject:
	- Python Interpreter > +(add) 
		- PyQt5, 
		- PyQtWebEngine (webbrowser into your widget)
		- QDarkStyle
	- Project Structure

## `pip install pyqt5 pyqt5-tools`
`pip install PyQt5`

cmd > `python --version`
```powershell
C:\Users\jarek>python
Python 3.11.0 (main, Oct 24 2022, 18:26:48) [MSC v.1933 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print(sys.executable)
C:\Users\jarek\AppData\Local\Programs\Python\Python311\python.exe

```


```shell

$ python3 -m venv ./venv
$ source venv/bin/activate
(venv) $ pip install pyqt5 pyqt5-tools
```

>
>Windows: `venv\Scripts\activate`, `venv/Scripts/activate`
>


or use  PyCharm
- you have your project made
- settings > Project> Python interpreter> '+' > write: `PyQt5` and install: `PyQtWebEngine`, `QDarkStyle`




