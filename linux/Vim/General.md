#vim/windows 
#vim/terminal

### vim awesome
https://vimawesome.com/



`:ter` open horizonal split terminal
`:vert term` open vertical terminal

-----
błąd z puginami, rozwiązany (nie do końca)
```bash
cd ~/.vim/bundle/YouCompleteMe/
sudo pip install cmake
python install.py

```
-----
:PluginInstall

(blokada przewijania terminala a terminal scroll lock)  
->  
`ctrl+q  `
odblokowuje vima  

.vmrc  
#vim/vmrc 

"-komentarz

```vim
set t_Co=256-ustawienie pracy w 256 kolorach  
"liczba spacji po tab ustawiona na 2  
set softtabstop=2  
set: showmod-pokazuj mode w którym pracujesz  
highlight Normal ctermfg=grey ctermbg=black  
highlight Comment ctermfg=grey
```

**instalacja i konfiguracja vima**  

ze strony [https://github.com/ets-labs/python-vimrc/blob/master/README.rst](https://github.com/ets-labs/python-vimrc/blob/master/README.rst "https://github.com/ets-labs/python-vimrc/blob/master/README.rst")  
 

`sh -c "$(curl -fsSL https://raw.githubusercontent.com/ets-labs/python-vimrc/master/setup.sh)"`
