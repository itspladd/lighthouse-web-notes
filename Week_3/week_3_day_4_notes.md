# Security, Encryption, and Hashing

PLAINTEXT STORAGE IS BAD!
We could encrypt it, or we could hash it.

Hashing is not reversible!

Hashing takes a "salt" and the input password, and the "hash function" iterates over the password many times, resulting in a "hashed" value.

Each iteration doubles the time it takes to hash the content

We will be using **`bcrypt`** to hash our passwords!

## bcrypt

`bcrypt` has both async and synchronous options. Normally you'll use async, but for TinyApp, we'll be using the synchronous option.

## Cookie Security

If your cookies are plaintext, someone could just change their cookie so thtat they look like someone else.

In this case, hashing the cookie over and over would take up too much performance power! So instead, we use **encryption**.

The encrypted cookie will be saved as a `user session`. This session is internal to our code, and stores the data about the user.

## Cookie Theft and HTTPS

Someone could steal our cookies if we're not careful! HTTP is in plaintext, and someone could intercept the cookie data as it's being sent.

**HTTPS** encrypts the information as it is being sent.

# REST

True RESTful architecture uses the actual `GET`, `POST`, `PUT`, and `DELETE` verbs.

## Nested Resources

If you have a resource appended to another resource, that's a `nested resource`

```
/quotes/:id is a resource
/quotes/:id/comments is a nested resource
```

# Middleware

**`Middleware`** sits in between a request and a response. It's just functions that operate before a response is sent!

Each piece of middleware calls the next piece of middleware, until the chain is completed and the response is sent!