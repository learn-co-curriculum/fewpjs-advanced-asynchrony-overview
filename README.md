# Advanced Synchrony Overview

## Looking Back

Earlier in our front-end web programming journey, we learned about the
asynchronous model of program execution. In this model, functions can perform
tasks while other tasks are completing in the background. This creates the basis
for the efficient experience JavaScript provides for web users—without it, we
would be waiting for animated gifs to load or audio to continue to stream while
browsers finished responding to an earlier request.

To implement an asynchronous model in JavaScript, we learned how to use the
Fetch API. The process of using `fetch()` gives us these steps:

- Make a request
- Handle the data sent back
- Handle any errors the server sends

In code, it looks something like this:

```javascript
fetch('http://example.com/log_dogger', configObj)
	.then(function(response) {
		return response.text();
	})
	.then(function(content) {
		if (response == 'OK') {
			console.log('Added a new dog!');
		}
	})
	.catch(function(error) {
		alert('Bad things! Ragnarők!');
		return 'This is an error message. There are many like it, but this one is for log_dogger';
	});
```

## Looking Ahead

Now that we know how to implment an asynchronous model using `fetch()`, it's
time to dig a little deeper into exactly how it works and why. We're going to
see how we conceptualize the process and replicate it without using `fetch()` at
all. We'll also gain a stronger understanding of Promises by taking a look at
the Promise API. By the end, you'll be able to construct asynchronous JavaScript
code that is both optimized and lightning fast.
