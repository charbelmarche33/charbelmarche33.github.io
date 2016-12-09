---
layout: post
title:  "Socket IO and Creating Dynamic Web Apps"
date:   2016-12-10 10:51:11
categories: blog
---

If you check out many professional websites you can notice that many of them do not reload everytime that the page wants to change a portion of its content. This is an integral part of many websites such as Amazon, Yahoo, Youtube, and many others. 

The way that we can make our websites interact with the user with out having to reload everytime is by using Flask Socket IO--which gives flask applications the ability to access low latency bi-directional communications between the clients and the server. This essentially makes allows you to use JavaScript functions which are called by html actions like this:

```
<form method = 'POST' ng-submit="sendSearch()">
<p>Search Messages: <input type="text" ng-model="termToSearch"/><br/>
                  <input type="submit" ng-disabled="!termToSearch" value="Submit"/></p>
</form>
```

Here ng-submit defines the function that is called when the submit action is performed, ng-model gives the search textbox a name so we can access it, and ng-disabled basically enforces that for the submit to be clicked termToSearch has to have some value in it--it cannot be empty. Now this will run a function in the javascropt file (called controller.js) as shown below:

```
 $scope.sendSearch = function sendSearch(){
  console.log('Searching: ', $scope.termToSearch);
  socket.emit('search', $scope.termToSearch);
  $scope.termToSearch = '';
 }
 ```
 
 This function prints 'Searching: valueSearched' to the console and then emits to the server-side to a function with the key-name 'search'  and passes a parameter. Also notice how we accessed the text field termToSearch and set it back to an empty string. Now on the server-side we can do something like this:
 
 ```
@socketio.on('search', namespace='/iss')
def search(searchTerm):
    <some content>
    emit('results', {'text' : res['message'], 'name' : res['username'], 'first':False})
```

Here I have defined a function that gets the call from the javascript controller and manipulates the information and passes them back to the javascript side to a function with the key-name 'results' with a dictionary as a parameter.

The javascript function should look something like this:

```
socket.on('results', function(res){
    console.log(res);
    $scope.results.push(res);
    $scope.$apply();
    var elem = document.getElementById('searchPane');
    elem.scrollTop = elem.scrollHeight;
});
```

The 'console.log' statement prints the paramater that is passed back to the console, the '$scope.results.push(res); $scope.$apply();' lines update the results list with in the scope of the html page and apply updates the changes. 

Simple as that you can update different portions of your websites!

P.S. I will make another post detailing how to get your Socket IO set up.