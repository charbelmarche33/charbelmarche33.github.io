---
layout: post
title:  "Uploading your Resume to a Professional Website."
date:   2016-12-01 23:51:11
categories: blog
---

Hello guys, I know that many developers like to have professional websites that employers can look at (and be in awe of our brilliance), so I am making a post on how to create a link to your resume on a website.

This is rather easy to do, all you need to do (if you have been following along with creating flask websites) is add a 'files' folder in the 'static' and upload the resume.docx or .pdf file in that location. Then in your html page, you can add a link to your resume by doing something similar to the following:

```   
<a href="static/files/Resume.pdf" download>Download Resume</a>
```

In fact, since you are reading this: 

Here is my <a href="static/files/Resume.pdf" download>resume</a>!

Also, I recently found a little trick in the python documentation that allows for you to display the date that the resume (or any other file) was last updated. This can be done by using flask as seen in "Throwback to Some Basic Flask". In the function, you will need to pass render_template('someName.html') some more variables.

So:

```
    @app.route('/pathToHTMLPageWithResume')
    def someFunctionName():
        #content
        render_template('someName.html')
```

Will become:

```
    @app.route('/pathToHTMLPageWithResume')
    def someFunctionName():
        #content
        varInPython = 'some value'
        render_template('someName.html', variableNameToBeUsedInHTML = varInPython)
```

This allows you to use variables from the python server side, in the html file. This is done with:

```
<p>Interested in learning more? Here is a copy of my resume as of {{ResumeDate}}!</p>
```

Where resumeDate is the variable passed into the html file using flask on the server side.

So now we know how to pass in a variable to the html page, we can use this knowledge to pass in the date that our resume was last updated to the html file. This only takes a couple lines of code but I think it is really cool and effective:

```
    @app.route('/pathToHTMLPageWithResume')
    def someFunctionName():
        #content
        Time = os.path.getmtime('static/files/Resume.pdf')
        Time = time.strftime("%b %d %Y", time.localtime(Time))
        render_template('someName.html', ResumeDate = Time)
```

Here the line where we use os.path.getmtime(path) time gets the time in milliseconds since the epoch that the file was last updated. Obviously this isn't a useful thing to show your employer that your document was updated some massive number of milliseconds since 1970. So the next line formats the string so that the it is a string formatted like:

Interested in learning more? Here is a copy of my resume as of Nov 28 2016!

Now you have everything you need to put your resume on your personal website. So what are you waiting for? Go do it!

Also Happy December to all!

Citations:
<a href='https://docs.python.org/2/library/os.path.html'>https://docs.python.org/2/library/os.path.html</a>


