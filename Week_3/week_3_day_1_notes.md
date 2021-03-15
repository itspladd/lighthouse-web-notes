# Servers

## Agenda
* Web servers
* NodeJS servers
* Request/response
* ExpressJS
* EJS and scalability
* Sending information from Server to EJS

## What Are Web Servers?
A web server is just a program! It's a program that is able to give information to other computers via a network.

### A Person Behind a Door
Imagine a person in a closed room. They have a bunch of stuff! They have money, and cabinets full of cool stuff, and sheets of data. But they can't leave the room.

However, they have a list of instructions posted on the door! If you write a command on a piece of paper, they'll do the thing you asked (if they know how). They'll always send a piece of paper with the results of what you asked for.

This is, at a fundamental level, how servers function. The request/response interaction will always exist, regardless of platform.

## Theory and Concept
ExpressJS does a LOT of the heavy lifting for us, so we can focus on the fun stuff. But first, let's talk about what's going on under the hood.

### The HTTP Module
Node includes a module called `HTTP` that is specifically designed for creating web servers at a low level.

#### A Super Simple Server
```JS
// Set up some constants
const PORT = 8080;

// Require the server library
const http = require('http');

// Initialize the server
// The callback function takes in two parameters:
// The REQUEST and the RESPONSE
const server = http.createServer((request, response) => {
  // request: the piece of paper you slide under the door
  // console.log(request);
  // request is HUGE! Let's get just small pieces instead:
  console.log(request.url)
  console.log(request.method);

  // TCP: You connect and stay connected
  // HTTP: You connect, make a request, get a response, and disconnect!
  if (request.url === '/' && request.method === 'GET') {
    response.end('Howdy partner!')
  } else if (request.url === '/memes' && request.method === 'GET') {
    response.end('<h1>PIKA PIKA</h1>')
  } else {

  }
});

// Server needs to listen! Accessible at localhost:8080
server.listen(PORT, () => {
  console.log(`Server is listening at port ${PORT}!`);
});
```

That's...a lot! It's very granular and hard to scale.

Enter...**`EXPRESSJS`**

## ExpressJS

`ExpressJS` is a framework for building web applications! It's built on Node.js, but it offers more featurs, routing, middleware, etc. It cuts down on development time!

It abstracts a lot of the hard stuff away. Woo!

### Setting up a server with ExpressJS

```JS
const express = require('express');
const app = express();
const PORT = 8080;

app.get('/', (req, res) => {
  res.send('Howdy pardner!');
});

app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
})
```
That's it!

### Features
* If you try to request something that doesn't exist or if something isn't handled, it throws you an error!
* It can handle HTML text strings in the `response.send` parameter!
* There's more! We'll look at them later!

## Sending Files Instead Of Strings
A **`template engine`** is a way to dynamically create web pages! (Such as Jekyll). ExpressJS has a BUNCH of template engines that it supports by default, but we will be using: **`EJS`**, which stands for Embedded JavaScript.

## EJS
EJS reads from a folder called `views`. You also have to specify it in your Express app! But you don't have to `require` it, since we won't actually be writing `ejs` in our code.
```JS
app.set('view engine', 'ejs');

// ORDER DOES MATTER! req MUST be first, res MUST be second!
// We don't control what happens inside `get`, it will ALWAYS expect req, res. If you get an error that says "res.[thing] is not a function", that might be the problem!
app.get('/', (req, res) => {
  // If you have a file called 'home.ejs' in your 'views' folder, then this will load that file!
  res.render('home');
  console.log('We loaded the home page!');
})
```
Much easier! Now we can maintain the HTML (and the embedded JS) within the `.ejs` file!

### Status codes
`res.render()` automatically sends a 200 unless you specify a status code manually:
```res.statuscode(300).render('page');```

## Adding Logic!

`res.render()` takes two parameters:
1. (REQUIRED) The name of the file to be sent out
2. (OPTIONAL) An Object that is "shared" with the file in the first argument

Let's say we have an array of image URLs:

```JS
// Inside your server logic
//......
const imgURLs = ['https://....img.png',
'https://....img1.png',
'https://....img2.png',
'https://....img3.png'];

app.get('/info', (req, res) => {
  const templateVars = { name: 'Pladd', color: 'blue', age: '31', images: imgURLs };
  res.render('info', templateVars);
})
```
```HTML
//Inside your HTML page
<html>
  ...
  <ul>
  <li><%= name %></li>
  <li><%= age %></li>
  <li><%= color %></li>
  <li><%= imgs[0] %></li>
  </ul>
  <% for (let item of imgURLs) { %>
    <img src="<%= item %>"/>
  <% } %>
  
  ...
</html>
```
* `<%= %>` is a single value to be shown on the page
* `<% %>` is LOGIC to be executed
  * Every line of logic must be in its own tag!!

EJS converts the `<%= %>` into HTML based on the variables in the object shared with it! And it converts `<% %>` into Javscript code and runs it!

EJS is smart, and also stupid: it will look ANYWHERE in the `.ejs` file for those sequences! Inside quotes, inside tags, inside attributes, as properties, whatever!

EJS is like a translator: the person behind the door feeds each EJS file into EJS with the page's object file as its 'setting', and then it gets converted to HTML! 

## EJS is Just One Option
There's lots of template engines, and different frameworks will use different ones!

EJS is a **server-side** engine! It does the processing and sends the page to the client as a completed HTML.

Some engines are **client-side**, which rely on the client's hardware to process everything!

In general, **client-side** is currently more preferred (for reasons we'll get into later), but it's important to be able to use both!