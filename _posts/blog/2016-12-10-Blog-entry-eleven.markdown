---
layout: post
title:  "Setting Up Socket IO"
date:   2016-12-09 12:51:11
categories: blog
---

To be able to update your webpage with out having to reload it as I detailed in "Socket IO and Creating Dynamic Web Apps", you need to do a handful of things. To start off we need to install flask IO in your workspace by entering 'sudo easy_install flask-socketio' in the terminal. Then you need install the Socket IO library from flask in your server.py file :

```
from flask.ext.socketio import SocketIO, emit
```

Then you have to create a controller.js file (probably with the path static/js/controller.js). In the controller.js file you need to add something similar to this:

```
var <SOMEVARNAME> = angular.module('<SOMEVARNAME>', [])
.config(function($interpolateProvider) {
        $interpolateProvider.startSymbol('//').endSymbol('//');
    });

<SOMEVARNAME>.controller('<CONTROLLERNAME', function($scope){
var socket = io.connect('https://' + document.domain + ':' 
+location.port + '<SOMEVARNAME>'); 

    <functions in here>
});
```

Then in your html files add:

```
<html lang="en" ng-app="<SOMEVARNAME>">
```

and

```
<script src="js/controller.js"></script>
```

in the header. Then anywhere you want to call the functions that you create in the controller.js file, you need to surround with the following code:

```
<div ng-controller = "searchController">
    <content>
</div>
```

Now you should have all the knowledge you need to use Socket IO :) Good luck and have fun!!!