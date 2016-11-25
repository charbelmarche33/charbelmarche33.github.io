---
layout: post
title:  "Throwback to Some Basic Flask"
date:   2016-11-17 16:13:11
categories: blog
---

Ladies and gentlemen, I have never been much of a hipster but I have always wanted to have my own website. Just something about it us tempting. Maybe it is how little I knew about making a website that made me want to learn? Regardless, this fall I took an Applications of Databases class at the University of Mary Washingtonand I was both surprised and shocked that most of what we would be doing is web-based. Earlier that summer I had taken a job with UMW Enterprise Applications Services where I had to write queries to access information from this (what I thought at the time, later I learned there are much larger ones) massive database. I had to learn this language called SQL that was said 'sequel' but some rather than 'S-Q-L.' (My boss had tried this with me and I looked very stupid asking her what 'Sequel' was after spending the last few hours trying to learn it). I had the expectation that this class would be nothing more than writing queries to access some information, boy I was wrong--and glad, that just sounds boring. 

So the first project we had in this class was to make our own websites using a html template from online and flask to create a consistent interface for all our unique pages on the webpage. In case you are where I was before this class, yes you do not have to write all your HTML files from scratch. You can take other peoples work and no it is not plagarizing. 

We were working on Cloud 9, essentially and online Virtual Machine in which you can create your own workspaces for different projects. After I had a workspace up and running I installed flask in the shell with the following code:  'sudo easy_install flask markdown'. Once this was done I set out to find a good template for me to use. This is very easy to find all you need to do is search 'Free HTML Templates,' there are plenty out there, do not be stupid and force your self to do what you do not need to.

After finding a good template, I copied the zip file over to my workspace then unzipped it with 'unzip zipfilename.zip'. The template should have some premade html files with in it, what you will need to do is create a templates folder and a server.py file (if not already there). Move your layout.html file to the templates folder.

In the server.py, you want to have code similar to the following:

    import os, time, os.path, psycopg2, psycopg2.extras
    from flask import Flask, render_template, request
    app = Flask(__name__)
    
    @app.route('/')
    def mainIndex(): 
    PersonalInformation = {'Name':"Charbel Marche", 'Year':"junior", 'School':"UMW", 'GPA':"3.5"}
    return render_template('home.html',  selected='home', PersonalInformation = PersonalInformation)
                                         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^These are variables that you can access in your html file
    
    #This is an example of a function that renders the template 'another.html'
    @app.route('/someotherpathonsite')
    def functionName():
        ...some stuff..
        return render_template('another.html')
        
        
    #Start the server here
    if __name__ == '__main__':
    app.run(host = os.getenv('IP', '0.0.0.0'), port = int(os.getenv('PORT', 8080)), debug = True)
    
The cool thing about using flask is that you can make your website have a consistent interface, so for example we would have an layout.html file, as mentioned before. The body of that webpage can be replaced with the following code (from flask):

    {% block content %} {% endblock %}
    
Then in different .html files, you can do the following:

    {%extends "layout.html" %}
    
    {% block content %}
     //Some content in here
    {% endblock %}

Now you to customize the content of your different html pages, while maintaining the a consistent and appealing interface.