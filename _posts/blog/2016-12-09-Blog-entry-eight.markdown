---
layout: post
title:  "Logging In"
date:   2016-12-09 12:51:11
categories: blog
---

Say you had a website that allows for the user to log in. How would you store the username? How will the other webpages be able to differentiate if a user is logged in or not? Someone with out much experience in coding web applications may say use a global variable like so:

```
from flask import Flask, render_template, request, redirect, url_for, session
import utils, psycopg2, psycopg2.extras, os

app = Flask(__name__)
app.secret_key = os.urandom(24).encode('hex')

loggedIn = False;

@app.route('/', methods=['GET', 'POST'])
def mainIndex():
    return render_template('index.html', loggedIn=loggedIn)

@app.route('/login', methods=['GET', 'POST'])
def login():
    loggedIn = True
    return render_template('login.html',  loggedIn=loggedIn)
    
@app.route('/register', methods=['GET', 'POST'])
def register():
    return render_template('register.html',  loggedIn=loggedIn)
   
@app.route('/submitted', methods=['GET', 'POST'])
def submitted():
    return render_template('submitted.html', loggedIn=loggedIn)
    
@app.route('/logout', methods=['GET', 'POST'])
def logout():
    loggedIn = False
    return redirect(url_for('mainIndex'))

if __name__ == '__main__':
    app.debug=True
    app.run(host='0.0.0.0', port=8080)
```

Now while this may appear to work (of course you need to add content and a purpose to these pages, I am refering merely to the login/logout standpoint), it makes a crucial mistake of assuming that there is only one user logged in at a time. If another person where to log on and log out it would log both of the users out. Also if you were storing usernames and a user was to log on as 'John' then another log on as 'Jeremiah' then both will be logged in as 'Jeremiah' and as you can imagine this is a disaster. 

What can be done instead is using a session variable to store information locally, suched as if the user is logged in, their username, and many other things. How is this done is by importing flasks session library (the flask part):

```
from flask import Flask, render_template, request, redirect, url_for, session
```

Now when we store information into sessions variables they are stored with in the cache of the browser that you are using. This means that they are specific to the local system and we no longer have this problem.

How do we create a session variable you ask? Well let me show you:

```
session['keyValue'] = <data>
```

Now how can you use this information to make different interfaces in the html side depending on if someone is loggedIn? Well all you would have to do is pass the session variable into the html file using flask like this:

```
@app.route('/', methods=['GET', 'POST'])
def mainIndex():
    return render_template('main.html', name=session['name'])
```

and on the html side we need to do something like this as an example:

```
{% if name == '' %}
<h1>Create an account!</h1>
<form method = 'POST' action = '/submitted'>
    <table>
        <tr><td>Username: </td><td><input type="text" name="user_name" size="35" /></td></tr>
        <tr><td>Password: </td><td><input type="password" name="pw" size="35" /></td></tr>
        <tr><td>Area Code: </td><td><input type="text" name="areacode" size="35" /></td></tr>
        <tr><td><input type="submit" value="Submit"/></td></tr>
    </table>
</form>
{% else %}
<h1>{{name}} is already logged in!</h1>
{% endif %}
```

On the server side have this code at the beginning of each function:

```
try:
    print('User: ' + session['name'])
except:
   print("Noone is logged in.") 
   session['name']=''
```

This tries to print session['name'] but if it has not been set yet it instantiates it as an empty string (meaning that noone is logged in). Just a different way to keep track of if the user is logged in or not. When the user logs out just reset session['name'] to an empty string again.

I hope this helped you out! Happy coding!!!
