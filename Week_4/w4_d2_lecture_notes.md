# Client Side JavaScript and jQuery
## Agenda
* JS in the browser
* Broswer objects: window, navigator, document, and event
* DOM
* jQuery
* Element creation/DOM manipulation with jQuery
* Document Ready

## JS in the Browser
JS is as old as Netscape - it's been around for over 20 years!

There used to be two kinds of JavaScript: JScript for IE and JavaScript for everyone else. Thankfully, that's no longer the case.

## Browser Objects
### Window
* Each tab in a broswer is a window with its own `window` object

### Navigator
* Contains (public) information from the browser, such as location, version, browser type, "is this tab active?", webcam access, etc

### Document
`Document` contains all of the actual content in a page. It does NOT contain information about tabs, window size, etc. It's an object with all of the **content** of the page.

It also has methods for accessing and manipulating elements, such as:

* `getElementById('id')`
* `getElementsByTagName('name')`
* `getElementsByClass('class')`
* `element.innerText`
* `element.innerHTML`

...and so on.

BE WARNED: Many of these functions return a custom object called an `HTMLCollection`, which looks a lot like an array, but is *not* an Array object and does not have access to `.map`, `.forEach`, and other Array functions! 

However, it **is** iterable, which means you can use `for...of` loops!

#### **`querySelector`**
The new `document.querySelector` method lets you target elements based on a CSS selector! For instance:

* `document.querySelector('button:first-of-type')`
* `document.querySelector('.navButton')` returns the first instance of that class
* `document.querySelectorAll('.navButton')` returns **all** instances of that class!

#### **Events**
`document` can add Event Listeners to any part of the tree. Event listeners give a lot of information about user interactions! You can get the target element, the source element, the location of a click, or pretty much anything you want about the interaction itself.

## Document Ready
If your script tries to access elements before the page has loaded them, you'll get problem! The `document` object can tell us when it's ready to be interacted with, so it's best to listen for that event and have your code wait until that's done before you try to interact with it!

## jQuery
**`jQuery`** is a library built on JavaScript that aims to abstract away and streamline some of the complicated aspects of manipulating the DOM with JavaScript.

It uses a shorthand `$(' ')` (`jQuery(' ')` does the exact same thing) to access elements in a way very similar to `querySelector`, with a few differences.

* Get an attribute: `$('element').attr('attrName')`
* Set an attribute: `$('element').attr('attrName', 'newValue')` (works on ALL matching elements)
* Create an element: `$('<element>')`
* Create an element and set attributes: `$(<elem>).attr('attrName, 'val')`
* Add an element to another element: `$('target').append(element)`

If used properly, jQuery generally shortens and simplifies your code.