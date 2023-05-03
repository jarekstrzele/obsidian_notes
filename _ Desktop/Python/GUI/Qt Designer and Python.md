

https://realpython.com/qt-designer-python/#getting-started-with-qt-designer

>[!info] Qt Designer
>- a Qt tool that provides WYSIWYG user interface to create GUIs for your PyQt applications productively and efficiently 
>- Drag and drop QWidget objects on an empty form
>- allows to preview your GUIs using different styles and resolutions
>- is a platform and programming language independent
>- it doesn't produce code in any particular programming language, but it creates `.ui files` (they are XML files with detailed descriptions of how to generate Qt-based BUIs )

`.ui` -> `pyuic5` -> `.py` (?)

# Installing and Runing Qt Designer

```shell

$ python3 -m venv ./venv
$ source venv/bin/activate
(venv) $ pip install pyqt5 pyqt5-tools
```

Windows: `venv\Scripts\activate`


The installation will place the Qt Designer executable in a different directory according to your platform:

-   **Linux:** `...lib/python3.x/site-packages/qt5_applications/Qt/bin/designer`
-   **Windows:** `...Lib\site-packages\pyqt5_tools\designer.exe`

On Linux systems, such as Debian and Ubuntu, you can also install Qt Designer by using the system package manager with the following command:
```shell
$ sudo apt install qttools5-dev-tools
```

















