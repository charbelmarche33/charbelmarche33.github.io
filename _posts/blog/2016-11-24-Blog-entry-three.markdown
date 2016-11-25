---
layout: post
title:  "Passing in paramaters to Socket IO from flask--DO NOT MAKE THE SAME MISTAKE AS ME"
date:   2016-11-124 23:51:11
categories: blog
---

Hello guys, I am just writing this blog to potentially help anyone out here on the web that comes across the same problem as me. If you are working with flask and have a for loop of different values in a list, like so:
{% blockquote %}
    \{\% for room in rooms \%\}
           <button ng-click="changeRoom('{{room.room_name}}')">{{room.room_name}}</button>
    \{\%endfor\%\}
{% endblockquote %}

If you want to pass a different paramater into the same function for each button, you have to make sure that you put the quotes around the object that you want to pass in. I literally sat there for hours trying to figure what wasn't working.

The reason you have to do this is because if you do not, Angular JS will think that whatever value room.room_name is, is a variable referring to a name of an html block as opposed to passing in a string (if it originally was a string).

So please guys, do not make this mistake and if you did I feel your pain.
