[[_ 0 Python Tkinter GUI]]


```python
from tkinter import *
from tkinter.ttk import *
import time

win = Tk()

percent = StringVar()
text = StringVar()

bar=Progressbar(win, orient=HORIZONTAL, length=200)
# bar=Progressbar(win, orient=VERTICAL, length=200)
bar.pack(pady=10)

def start():
    tasks = 10
    x = 0
    bar['value']+=10
    while(x<tasks):
        time.sleep(1)
        bar['value']+=10
        x+=1
        percent.set(str(int((x/tasks)*100)) + "%")
        text.set(str(x) + '/' + str(tasks) + ' tasks completed')
        win.update_idletasks() # to refresh window

percent_lbl = Label(win, textvariable=percent).pack()
task_lbl = Label(win, textvariable=text).pack()
btn=Button(win, text="download", command=start).pack()

win.mainloop()
```
















