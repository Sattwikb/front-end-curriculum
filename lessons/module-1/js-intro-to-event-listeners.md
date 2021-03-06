---
title: "JS: Intro to Event Listeners"
length: 120
tags: javascript, dom, events, event listener, event handler
---

## Learning Goals

* Continue to develop a basic understanding for JavaScript syntax
* Understand how to attach event listeners to DOM elements
* Understand how to write event handler functions

By the end of this lesson, you'll be able to customize a user's experience on a small site based on some input they provide. Below is a giphy of this type of experience in action:

<img class="medium" src="./assets/images/dom-manipulation-1/greeting-app.gif">

Before we can implement functionality like this though, we're going to build a strong foundation and understanding of the tools that help us do that.

## Vocabulary

- `Event` Any event which takes place in the DOM, these can be generated by users or the browser.
- `Event Listener` A function invoked on a DOM node which fires the `event handler` when a specified event occurs on the node or its children
- `Event Handler` A function that will run when a specific event occurs

## Warm Up

On your own, answer the questions associated with each stage of the Greeting App. If you aren't sure - it's ok - but take a try. You'll have time to chat with your partner afterward.

[Jamboard](https://jamboard.google.com/d/1iMb2VuJopHXVTa5wRDg6sPDM-bhwpPjFiAL9FGnB-ZY/edit?usp=sharing)

<!-- [Instructor Resource](https://docs.google.com/document/d/1NmlZD0IlsInu4zjpCey9MI2GdV-Zd_jlIcnLdcvnTEo/edit) -->

## Event Listeners

Changing stuff on the page with JavaScript is great, but you might as well have just written it in the markup to begin with. The real power of JavaScript comes into play when we write code that **responds to user input**.

This power emerges when we start **listening for user events**. This is the crux of front-end engineering. We present a user interface and then as the user interacts with the UI, we change and update what they see.

Let's take a look at the syntax and then we'll talk about what's happening.

<p class="codepen" data-height="300" data-theme-id="37918" data-default-tab="js,result" data-user="turing-school" data-slug-hash="MWWzMre" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="A First Event Listener">
  <span>See the Pen <a href="https://codepen.io/turing-school/pen/MWWzMre">
  A First Event Listener</a> by Turing School (<a href="https://codepen.io/turing-school">@turing-school</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

1. We're querying for all of the elements we need and we're storing them in variables.
2. We're adding an event listener to the `<button>` with the class of `.change-text`.
3. We're passing `addEventListener()` two arguments:
  - The type of event we're interested in listening for.
  - The name of a function that should be called whenever that event happens.
4. We declare the function that will be called when the button is clicked.

<section class="call-to-action">
## Explore

Open up a webpage that you often visit. Maybe it's a social media page, maybe it's your bank's website, maybe it's a news site. Take a few minutes and list all the event listeners that you think might be on that page! What do they do?

</section>

### Style Change on Button Click

Like we mentioned earlier, it's pretty common for a user to experience helpful feedback from an application after they've taken some sort of action.

Take for example the "heart" icon on CodePen. CodePen has 4 levels of "love" - 0, 1, 2, and 3. Each time a heart is clicked, the user increments their love up by one. (Until the click when it is read and at level 3 - at that point, it goes back to 0). While the "love leveling" is a bit confusing, this is still a great example of **styles changing based on user interaction**.

<img class="medium" src="./assets/images/dom-manipulation-1/codepen-heart-click.gif">

To do this, we need to combine what we just learned about event listeners with what we learned about changing styles programmatically earlier in this lesson.

<section class="call-to-action">
### Pair Challenge

We are putting a few pieces together now, so this may seem a bit more challenging. That's when it is especially important to pseudo-code, or write human-readable notes that give you a roadmap for the code you will later write.

Your task is to create a single `div` that is gray. Then, when it is clicked, it turns pink!

In your notebook:
* List the directions, as specially as possible, that you want to give to the computer.
* What are the DOM elements that this program will need to know about? What variable names will you use for them?
* What CSS styles might you need to create?

Now, implement your ideas in code.

**Extra Time?**

If you have extra time, think about and pseudcode what you would need to do to build out the full CodePen heart:   
- when clicked, the gray `div` turns pink
- then on another click it turns deeper pink
- then when clicked again, it turns red
- then when clicked again, it returns to being gray
</section>

Now, get together with another group and discuss your approaches. This is not a time to share "solutions" or "answers", but instead to talk about how you went about breaking down the problem. Did you pseudocode? Did you look up any documentation? What did you google?

### Get User Input

We can use the `.value` property available on an `input` DOM element to get the value that a user has typed into it.

<section class="call-to-action">
### Explore

Follow the steps below to explore how `.value` works!
1. Open your dev tools and inspect this box, specifically, the input field below. What is its class name?
2. In the console, call `document.querySelector('.check-me');`
3. In the console. call `document.querySelector('.check-me').value;`
4. Type your favorite food into the input
5. In the console. call `document.querySelector('.check-me').value;`

<input type="text" class="check-me" placeholder="this is the input!">

</section>

When called, the `.value` property on an input element will return the **current value**.

<section class="note">
One of the top misconceptions/mistakes we see students make while in Mod 1 is attempt to capture the value of an input while the input is empty. If you want to get a user's input, we have to get the value **inside of some event listener** - on an event that happens after the user has typed into the input field.
</section>

Below is an example of a small application that takes a user input, then changes the color of a box based on that input:

<p class="codepen" data-height="300" data-theme-id="37918" data-default-tab="html,result" data-user="turing-school" data-slug-hash="bGGeKVa" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Color Box">
  <span>See the Pen <a href="https://codepen.io/turing-school/pen/bGGeKVa">
  Color Box</a> by Turing School (<a href="https://codepen.io/turing-school">@turing-school</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Let's break down what's happening in the CodePen above:
- **Lines 1-3:** Declare variables for the DOM elements that we will need (box, input field, button)
- **Line 5:** Attach an event listener to the button
- **Line 7:** Declare a function that will execute when the button is clicked
  - Declare a variable, `color` that takes the value the user selected and stores it
  - Applies an inline style, `backgroundColor` with that newly selected color

<section class="call-to-action">
## Solo Practice

Fork [this CodePen](https://codepen.io/turing-school/pen/abbQeoG) and implement these two features:
* When the user clicks on the "Change Text!" button, the `innerText` of the `h1` should change to be the contents of the input field.
* When the user clicks the "Change Styles!" button, it should adjust that property on the box.
<br>

Here is an example of the second task:

![Custom CSS Color Box](https://s3-us-west-2.amazonaws.com/s.cdpn.io/t-340/custom-css-modifier.gif)

</section>

<section class="call-to-action">
## Greeting App

Take 5 minutes with your partner to share your jamboards from the Warm Up.

Then, fork [this CodePen](https://codepen.io/kaylaewood/pen/ZEOOKOG) and start building out the Greeting App. Start with writing the HTML, then add the functionality. Handle the styling after the app is working as expected.

</section>

### Suggested re-teaching practice

When you study event listeners, here are some suggested exercises:

- Look up what some common event listener types are (you've already seen `click`!)
- Read up on the [event listener documentation](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)
- Create a codepen with some HTML elements, and make up some event listeners for them! Try turning a red square green when it gets clicked. Try getting the data from an input field and displaying it on the page.
- In Codepen, create a simple webpage with a night-mode toggle button!
