---
title: AJAX: Making the web snappy and dynamic
length: 90min
tags: ajax, javascript, front-end
---

![I hate it when I'm studying and a velociraptor throws bananas at me](http://turing.lynn-miller.com/autosuggest.gif "I hate it when I'm studying and a velociraptor throws bananas at me")

### Goals

By the end of this lesson, you will:

* Know what AJAX is
* Know when to use AJAX
* Know how to use AJAX

### Structure

#### Hook:

* Have you ever filled out a registration form only to have it tell you after you’ve submitted it that the username you requested is already taken? Wouldn’t it be great if the form told you if what you entered in the username box was available, and it did that every time you changed the entry, and without reloading the entire page (which would take forever)? What if you had to reload Gmail to see if you got a new message, or hit a ‘next’ button to see more Facebook posts? Enter AJAX.
* AJAX doesn’t make the web; it makes the web better, faster, more responsive. In the last decade AJAX has gone from a rare feature to a necessary fundamental, and that trend only seems to be continuing. Modern single page applications (SPA’s) largely rely on AJAX to work. AJAX is everywhere, from Gmail to Facebook to chat boxes to StackOverflow.

#### Opening:

* Don’t let the name scare you
* AJAX is about the browser exchanging little bits of information with a server (yes, it can be more, but we’re going to focus on that aspect for now)
* The goal of AJAX in web development is to prevent reloading an entire page in order to transfer a small amount of information
* AJAX consists of a bunch of calls and responses
* I’m going to teach you how to build a StackOverflow style voting system

#### Introduction to New Material (I do)

* There’s a lot of back-and-forth (state) which you don't have to deal with much these days
* There’s lots of systems for doing AJAX (XMLHttpRequest, fetch, jQuery). It doesn’t matter which one you use, the concept is always the same
    * You request a “resource”
    * There’s a delay -- maybe other stuff can happen during that time, maybe not
    * You receive some sort of response


#### Guided Practice (We do)

* (code-along) Make an AJAX request from the console in Chrome
* QA

```javascript
fetch('http://turing.lynn-miller.com/randomquote').then(function(response) {
	return response.json();
}).then(function(quote) {
	console.log(quote);
});
```

No AJAX
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>Simple AJAX example</title>
	</head>
	<body>
		<div id="quoteBox">"Perfection is achieved, not when there is nothing more to add, but when there is nothing left to take away." ~ Antoine de Saint-Exupéry</div>
		<form id="quoteForm" method="POST">
			<textarea id="random" name="random" rows="5"></textarea>
			<br />
			<input id="submit" name="submit" type="submit" value="Get another quote">
		</form>
	</body>
</html>
```

With AJAX
```javascript
document.getElementById('quoteForm').addEventListener('submit', function(e){
  e.preventDefault();
  fetch('http://turing.lynn-miller.com/randomquote').then(function(response) {
  	return response.json();
  }).then(function(quote) {
  	document.getElementById('quoteBox').innerHTML = quote;
  });
});
```

#### Independent/Pair Practice (You do)

* We’re going to build a quote board. We’ll all be sharing the same quote board/backend. Make a system that (all without reloading the page):
    * Lets users add new quotes
    * Checks for newly added quotes every second
    * When the user clicks the “up” arrow next to a quote, it increments that quote's score, when they click “down” it decrements it
    * Bonus: Keeps the quotes ordered by score


#### The Closing:

* Check for understanding
* Discuss any clarifications or student misconceptions
* Review goals, further resources, and next steps

### Possible questions and/or misunderstandings

* What happens if a call fails
* Asynchronous code
* Might mistake an implementation for the only way

### Concepts:
* Synchronous/asynchronous
* Promises
* Client-server model
* JSON
* Polyfill
* Callbacks
* Request headers & CORS (sigh)
* Security (trusting data, XSS, etc)

### Slides

* [Link to optional slides]()

### Video

* [Link to optional video]()

### Repository

* [Link to optional repo]()

### Outside Resources / Further Reading

* [Link to first outside resource]()
