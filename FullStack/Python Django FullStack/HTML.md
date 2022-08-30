[[JavaScript]]
[[Python basic]]

do podręcznika tech:
[[Formularze]]

---

# Section 3-4 HTML
#html



## FORM
```html
<form method = "post">  

      <input type="text" name="theNameAssignedTothisInput" value="default value placed inside there">  

 <!--
	type="email"  
	type ="password"  
	type ="submit"
	value="Click me"  
    type="color"                    
-->
  </form>

```
---

New features of these input types:  
-   actions  
-   labels

**action**
```html
<form>  
	<input type="email" name="useremail" value="">  
	<input type="submit" name=" " value="Submit">  
</form>

```
if you submit some email 
(`[user@gmail.com](mailto:user@gmail.com"mailto:user@gmail.com")')`,
the email will be seen in URL 
`...forms.html?useremail=user%40gamil.com`

```html
<form action="https://www.facebook.com" method="get">  
      <input type="text" name="user" value="">  
      <input type="submit" name="" value="Submit">
	<!-- when you submit, you will redirect to facebook  
	-->
</form>
```
but in the URL `"https:/[facebook.com/?user=Written_text`

**label**
```html
<label>  
      Enter text:  
      <input type="text" name="" value="">  
</label>  

<label for="userinput">Enter input   
      Enter text:  
      <input id="userinput" type="text" name="" value="Hello">  
</label>  

<!-- PLACEHOLDER  -->
<input id="userinput" type="text" name="" placeholder="Hello">  
<input id="userinput" type="text" name="" placeholder="Hello" required>

```

```html
<select>  
      <option value="cc">Credit card</option>  
      <option value="pp">Paypal</option>  
</select>  

	<input type="radio" name="over" value="yes">  
	<input type="radio" name="over" value="no">

```




