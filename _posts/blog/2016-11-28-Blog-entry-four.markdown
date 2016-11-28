---
layout: post
title:  "Using Bootstrap Templates with Flask"
date:   2016-11-28 23:51:11
categories: blog
---

When I wrote "Throwback to some basic flask", I showed you guys how to create your own website with flask and an html template. If you have went out and done it you might have came out with a pretty decent looking website, but then you go to a professional website and might wonder how you can make your website look even better. Well again, lucky for developers like me (and maybe you) there are people who create bootstrap templates and allow the web to have access to (some) of them for free. What is Bootstrap? Bootstrap is html, css, javascript framework that you can use as basis for creating web sites or web applications. It makes responsive, mobile first projects. In normal people terms--it makes making cool looking, professional websites easy for the average developer.

So now that we know that this is, lets actually get our hands dirty and actually do this! All you need to start (using Cloud 9 of course) is to search for a free bootstrap template online then download it, copy it into your workspace, then unzip it. Once you have it unzipped, you need move the html files to a templates folder, create a server.py file as in the "Throwback to Flask Blog", put the CSS, JS, img, and fonts folders in a 'static' folder. Then you have to go through and fix all the paths in the html files for the references to the images, css files, and js files. Once that is done you can run your server.py file (make sure you are rendering a html file that exists in the bootstrap project) and look at the webiste. From then on out all you are doing is adding your content with in the html files. Also note that most bootstrap templates have different elements and cool features that you can use to display your content with in, so make sure to take note of this when you are adding your desired content/looking for a template.

Once you have all this done, it really is just a matter of using basic flask and html principles to add you material to your website and now that you know how to make your web apps look professional with minimal effort--happy coding!