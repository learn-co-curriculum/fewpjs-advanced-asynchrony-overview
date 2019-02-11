# Advanced Synchrony Overview

## Looking Back

Earlier in our front-end web programming journey, we encountered code that runs
_asynchronously_. Functions like `fetch()`, `setTimeout()`, and `setInterval()`
require us to think asynchronously: that is the code doesn't necessarily run
in the top-down, left-to right formate that _sycnhronous_ code does.

The asynchronous model of program execution allows functions to perform
tasks while other tasks are completing in the background. This creates the basis
for the repsonsive experience JavaScript provides for web users &mdash; without it, we
would be waiting for animated gifs to animate or audio to continue to stream while
browsers do  "behind the scenes" work.

Code that implements an asynchronous model in JavaScript tends to follow the following
general pattern.

- Start an asynchronous activity
- Wait for a success signal / Handle the data sent back in the success case
- **OR** Wait for an error signal / Handle any data / error messages the server sends

The process of using `fetch()` uses this framework:

```javascript
let configObj = { option1: "...", option2: "..." }

fetch('http://example.com/log_dogger', configObj)
  .then(function(response) { // Success case
    return response.text();
  })
  .then(function(content) {
    if (response == 'OK') {
      console.log('Added a new dog!');
    }
  })
  .catch(function(error) { // Error case
    alert('Bad things! Ragnarők!');
    return 'This is an error message. There are many like it, but this one is for log_dogger';
  });
```

To this point you might have used `fetch()` but you've never dug into the technology that
makes its simple patterns work. For example, what's the class (**HINT**: the `constructor`
function will help!) that's returned from those `then()` calls? Maybe you disagree and think
that `fetch()` is complicated and confusing. In this module we'll see what the alternative is.

Through this experience you'll come to appreciate asynchronous execution models
in event-driven (click, swipe, double-tap) contexts. Understanding this model and some of its
complexity will set you up to be successful in the browser; however, these patterns have also
been integrated into iOS / Swift as well as Android programming. The complexity of modern
programs requires _us_ to evolve our thinking in interesting ways!

<figure>
  
![David Tenant as "Dr. Who" on Time](https://media.giphy.com/media/M6VxE9CEHMDtK/giphy.gif)

<figcaption>David Tenant as "Dr. Who" on Time</figcaption>
</figure>


## Looking Ahead

Now that we have refreshed how to implement an asynchronous model using `fetch()`, it's
time to dig a little deeper into exactly how it works and why. We're going to
see how we conceptualize the process and replicate it without using `fetch()` at
all. We'll also gain a stronger understanding of Promises by taking a look at
the Promise API. By the end, you'll be able to rewrite `fetch()` from scratch by yourself.
