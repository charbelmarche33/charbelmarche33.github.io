---
layout: post
title:  "Phew.. Just Set Up My Blog"
date:   2016-11-15 16:51:11
categories: blog
---

Took me a while, but I finally have a blog up and running! How did I do this you ask? Maybe you are interested in joining me in the awesome privilidge and opportunity of having an online home like this? Well its really simple! Let me teach you how!

First things first you need to make a Cloud 9 account and create a workspace just for your blog. Then you need to install jekyll by enterning into the bash shell "gem install jekyll". 

Now you need to go find a cool jekyll template that you like and want to base your blog off of. This is very easy--unless you are indecisive like me--all you do is find a template you like and download it. Then you can take the zip file and upload it to your c9 workspace. Once it is in your workspace, unzip the file by entering into the bash shell "unzip (nameofzipfile)". Once this is done cd into the new unzipped folder and type in "jekyll build" into the bash shell. This should convert all the markdown files into html files (thus allowing you to customize the template). 

Now that you have this set up you need to link the workspace to a github repository. Log into github and create a new repository with the name (yourusername).github.io. For example mine is charbelmarche33.github.io and my username is charbelmarche33. Then when you have that set up go back to your c9 workspace and make sure you are in the folder that was created when you unzipped your template and type in "git init". Then type in "git remote add origin (linktorepository)." This should be provided by github itself. Then enter "git add -f *" to add files not in the repository, "git commit -m "Commit message here"" to send commit message, and "git push -u origin master" to push to the repository. Then you should be able to enter your credentials, then you site should be published!