[[_ Intro Scalable Web Applications with Python, Flask and SQLAlchemy]]

  
---

# Forms - flask - working with
ToDo:  
1. auth package(`__init__.py`, `blueprint`)  
2. routes.py  
3.templates folder  
4.forms.py  
 

## Flask WTForms 

`pip3 install Flask-WTF  `
 
**request object**  
GET:  
- the request object all the details of the request sent by the user of  
- request.args{ name='john', greeting='hello' }  
 

POST  
request.form{ user='harry', password='fsfsd'}  
 

form.hidden_tag()security fiture against CSRF  (Cross Site Request Forgery )  

`pip3 install flask_login ` 

`pip3 install flask_bcrypt`  

  

DataRequired --- filed can not be blank  

   

## TO COLLECT DATA FROM USERS WE NEED:  
1. FORMdef RagistrationForm(FlaskForm)  
2. ROUTElocalhost:5000/register  
3. TABLEclass Users(db.Model  
4. HTML PAGEregistration.html


















