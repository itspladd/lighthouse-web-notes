# CRUD With Express

## Recap: 3-Tier Architecture
* The `web browser`'s primary function is to render html
* The `server`'s job is to accept HTTP requests and send back resources
* The `database`'s job is to keep data persistence and allow CRUD (create, read, update, delete) operations

## Recap: ExpressJS
ExpressJS is a framework on top of node, providing:
* A routing system to get where we need
* A templating engine to create pages
* Middleware functions to do more things in the middle faster!

## CRUD with Express
Today's project: a movie quotes app! It neds to be able to:

* Create new quotes ->(C)
* List quotes ------->(R)
* Update new quotes ->(U)
* Delete quotes ----->(D)

### Middleware: Morgan
**`Morgan`** allows us to log requests to the terminal