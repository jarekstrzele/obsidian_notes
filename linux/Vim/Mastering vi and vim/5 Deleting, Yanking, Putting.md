[[_ Intoduction]]

---
 # Deleting, Yanking and Putting**   

  [[usun, dodaj, wstaw]]

`d/x`              cut text (cut = delete and save into a register)  
`register`      is a clipboard-like storage location  

`dd`     cut a line  
`p`       past a line under a cursor  
`shift +p `      past a line in the cursor place  

 standard           |              vim  
 --- | ---
    cut   |   delete   `d`  
   copy   |   yank     `y`  
  paste   |   put      `p`  


## R E G I S T E R  
#vim/register 
`^J` in the register means "new line"
### unnamed           
-  `""`  
-   holds text from d,c,s,x, and y operations  the most use

### numbered         
- `"0    "1    .... "9`  
- `"0` holds last text yanked  
- `"1` holds last text deleted (d) or changed (c)  
- numbered registers shift with each d or c  


`:reg` [register(s)  
`:reg 1`  
`:reg 1 z`  

**UNDO**  
`u`  

**REDO**  
`ctrl r`


**to paste**
`"` + register_number+`p`
past from register 2: `"2p`



### named  
`"a .. "z`

to yank entire line to the register `a`: `"ayy `
to paste `"bp`
to append more tekst to the existied register use a capital letter of the register name (i.e. `"Byy`)


to **see contents** of registers:
`:reg register_name`
`:reg b`
`:Reg 0 1 b`

### Repeating with register
`[count][register]operator`
or
`[register][count]operator`

`2"hp`  paste twice content of `h` register








