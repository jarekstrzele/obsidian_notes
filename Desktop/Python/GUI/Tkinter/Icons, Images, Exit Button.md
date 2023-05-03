[[_ basics GUI Python]]

https://iconarchive.com

```python
import tkinter
from PIL import ImageTk, Image # pip install Pillow

root = tkinter.Tk()
root.title('Learn')
# root.iconbitmap('sun.ico')

button_quit = tkinter.Button(root, text="Exit", command=root.quit)
button_quit.pack()

img1 = ImageTk.PhotoImage(Image.open('sun.ico'))
img_lbl = tkinter.Label(image=img1)
img_lbl.pack()

root.mainloop()
```


`my_lbl.grid_forget()`
`my_btn.config(state="DISABLED") ;`










