# Cookies
HTTP and browsers are **stateless** by nature, which means that they don't have the capacity to remember previous actions and apply that context to future actions.

**Cookies** are a solution to this problem: a website instructs the browser to save a small file with information about your site interactions, which the website can check on future interactions.

## Cookie Structure
Cookies are saved as **key/value** pairs! They're accessible in the headers, but they're not saved in nice JSON notation; they're just a big string blob!

```
// In the header
cookie: "username=Bob; userID=513; favorite-color=Green"
```
Writing our own code to extract data from this would be tiresome and give us yet another thing to maintain - good thing someone else already made a parser for cookies!

## Parsers
A **cookie parser** takes the cookie data and turns it into an object we can use!

```JS
// Once a parser is installed...
// req.cookies is an object!
const userID = req.cookies['userID'];
const userName = req.cookies['username'];
const color = req.cookies['favorite-color'];
```

## Login Logic
Once we have the cookie, we can check for the existense (or truthiness/falsiness) of certain cookie elements - like a `userID` - to see if the current session is logged in or not! And if they're not, then we can hide certain data from them!