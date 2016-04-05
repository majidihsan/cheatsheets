
JavaScript:
-----------
https://www.cheatography.com/davechild/cheat-sheets/javascript/

Helping material:
-----------------
http://www.dummies.com/how-to/content/javascript-ajax-for-dummies-cheat-sheet.html

http://blueblots.com/development/ajax-and-javascript-cheat-sheets/


Implementing AJAX functionality in a web application:

User interacts with the page (via clicking on some element in the Document Object Model, or DOM).
This triggers a JavaScript event handler (e.g.- function(event) {}), which makes a HTTP request to the server.
When the server responds to the HTTP request, a JavaScript callback function is executed (e.g.- request.done(function() {})), which updates the DOM.


JavaScript Objects:
------------------


// Object Literal
------------------

var person = {
 firstName: "Barry",
 lastName: "Zuckerkorn",
 name: function() {
   return this.firstName + " " + this.lastName;
 }
}
console.log(person.name())


var garfield = {
 name: "Garfield",
 color: "orange",
 greet: function() {
   console.log("Meow there, my name is Garfield");
 }
}


DOM Data Types:
----------------
document
An object-oriented representation of the document we're looking at
element
a single HTML tag & its contents
<title>Google</title>
nodeList
A collection of elements
attribute
Same as an attribute on an HTML tag
href="http://google.com/“
Google
Search the world's information, including webpages, images, videos and more. Google has many special features to help you find exactly what you're looking for.


Grab Elements:
---------------

document.getElementsByTagName("body")[0];
document.getElementById("oh-hai");
document.getElementsByClassName("whats-up");


// createElement
// appendChild

var appendElement = function(target, tag, text) {
 var element = document.createElement(tag);
 var textNode = document.createTextNode(text);
 element.appendChild(textNode);
 target.appendChild(element);
}

var body = document.getElementsByTagName("body")[0];
appendElement(body, "p", "Make it Dynamic!");

var body = document.getElementsByTagName("body")[0];
body.appendChild(paragraph);


// Capture user interaction with the "New Fortune" button.
// Prevent the default behavior, and submit an AJAX GET request.
$("#new-fortune").on("click", function(event) {
 event.preventDefault();

 var request = $.ajax({
   method: "GET",
   url: "/new-fortune.json"
 });

 // Upon a successful response, insert the new fortune into
 // the DOM.
 request.done(function(newFortune) {
   $("#fortune").text(newFortune["fortune"]);
 });
});
