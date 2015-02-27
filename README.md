# JQuery/Ajax Quiz

Write your answer below each question.

### Question 1
(a) What is a click handler?

A click handler uses jquery to perform an action/function when an element of the page is clicked.

(b) Where in your JS file should you put it, and WHY?

In the document ready, as it's dependent on the document loading before it can functionand act on the DOM.

### Question 2
If you get the error `$ is undefined`, what does that mean and what could you do to fix it?

It means you haven't (or haven't properly) linked to jquery in your html file. Doing so should fix the problem.

### Question 3
What should go in the `$(document).ready()` part of your JS file?

Anything that is dependent on the entire document loading to work and to act on/manipulate the DOM.

### Question 4
In an AJAX GET request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent?

```
$.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
```
The data in the above example would be the data returning from the server - in this case from Hacker News - usually in the form of JSON. In this example it would be a list of all of the users in the database.

### Question 5
In an AJAX POST request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent? (Hint: it's not the same as in Question 4.)

```
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'POST',
    dataType: 'JSON',
    data: { user: { name: "Anna", about: "instructor", email: "hi@gmail.com" } },
  })
  .done(function(data) {
    console.log("success!");
  });
```
The data in the above example, from an AJAX POST request, would be the data (one user) that the user has successfully submitted/posted.

### Question 6
Suppose you had the following form in your HTML file. Use jQuery to write a single line of code that takes whatever the user entered in the textbox and saves it to the variable `user_input`.

```
  <form>
    <p>The dress is:</p><input type="text" id="color">
    <input type="submit" value="Submit" id="submit">
  </form>
```
var user_input = $('#color').val();

### Question 7
This code looks like it works, but when you run it, you see that the `UserApp.add_all_users()` function executes but `console.log` displays `undefined`. What's wrong with the code?

```
UserApp.get_all_users = function() {
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
  UserApp.add_all_users(data);
};

UserApp.add_all_users = function(data) {
  console.log(data);
};
```
UserApp.add_all_users(data) needs to be inside the .done callback function, otherwise it doesn't know what data is as it's outside its scope.


