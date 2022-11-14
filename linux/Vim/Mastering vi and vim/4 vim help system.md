#udemy 
# section 04 The vim Help System   
#vim/help
To switch between the help window and the editing window use  

*ctr ww* 
*:help*                  *:h* is a shorcut  
**:help nam_of_command**
:help dd

Delete [count] lines [into register x] linewise.  
**[..] - is optional**  
>:help count
> - ctr+o back to the previous section  
> - ctr+i go forward   

:help linewise  

*another way:      the cursor on the 'linewise' and press ctr+]*  

:help :q  

ctr+g      location of the help file  == :f

:q            exit from the help  

:help :q (ctr+d => shows all command started by 'q')+ tab to move on the options
:help :qu (ctr+d => shows all command started by 'qu')+ shift+tab move back on
tab to move on the options  --> from wildmenu :h 'wildmenu'  

Using a caret symbo ' ^ ' is the same as "ctrl"  

:h ctrl-f  == :h ^f  
