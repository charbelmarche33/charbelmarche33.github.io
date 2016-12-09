---
layout: post
title:  "Multiple Submit Buttons For One Text Field"
date:   2016-12-07 12:51:11
categories: blog
---

Hi guys, so I was doing an assignment for a class of mine, and I came across a problem of having 2 sumbit buttons that run queries using text in one text field. Here is an example of a scenario where one would want to do this:

<img src="/static/files/whereintheworld.png"/>
 
I was getting errors thrown when I would try and check which button was pressed using:

```
if request.form['NameOfOneSearchButton']:
    <content>
elif request.form['NameOfAnotherSearchButton']:
    <content>
```

This was not working because when the program tries to access a button that was not clicked, the program would throw an error. After testing different things, I realized that the code above works fine if the user clicked the button that you are checking. In other words, the program only breaks when it checks if the user clicked the button that was not clicked. So a funny, but actual way to get this to work is to do this:

```
        try: 
            if request.form['NameOfOneSearchButton']:
                <content>
        except: 
            if request.form['NameOfAnotherSearchButton']:
                <content>
```

Really simple stuff, but it is a problem I am assuming one of you guys to come across and really hope this helps!