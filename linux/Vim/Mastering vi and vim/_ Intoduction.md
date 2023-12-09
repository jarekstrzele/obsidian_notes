#jason_cannon  #udemy  #vim 

----
# Mastering the vi and Vim Editors on the Linux, Unix, Mac, and Windows Operating Systems

[[4 vim help system]]
[[linux/Vim/Mastering vi and vim/5 Deleting, Yanking, Putting]]
[[6 Transformin and Substituting TEXT]]
[[6 Inserting, Changing, Replacing, and Joining]]
[[7 - Text Object]]
[[7 - Macros]]


## MODES:
-   normal  
-   insert                             i ;esc to leave  
-   comand-line:  
>:q            quit
>:w           write
>:wq         write and quit  


## Section3 Vim Essentials  
### NAVIGATION  COMMANDS  
[[0 _ Vim wprowadzenie]]
```
	 k  
 h      l 
     j  
```

**v**  
`ctrl + f`         page down   
`ctr + b`               page up  

`w`     word forward  ( **W** without interpunction)  
`b`      word back       (**B**  without interpunction)  

  
**^ | 0**          begining of the line (shift + 6)  
`$`               end of the line            (Shift 4)  
 
 `gg`        first line                              
 `:1`         (go to the first line)    
 `:12`   

`GG`        last line 
`:$`         (go to the end of the file)  
`10gg`    idź do linii 10  
`ctr+g`   info about the line and the cursor position  

  
## DELETING TEXT AND "THINKING IN VIM"  

**x**    deletes the character at your current cursor position  
**X**    deletes the character right before or the left of your cursor  

**dw**         deletes a word  
*operation{motion}*
	dw  
	       d = the delete operation  
	       w = the word motion  

**dd**       deletes entire line  
**3dd**    deletes 3 lines   

*[count]operation[count]{motion}*
5dw            five delete words  
5 = the count / how many times to repeat  
dw = the command (delete word)  
*d5w*      delete five words  
*2d3w*    delete the three words and repeat this operation twice  = d6w  

>**.**            repeat last operation  

**D**     delete from the cursor position to the end of the line             = **d$**  


---
