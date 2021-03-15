# Networking
* Q/A
* What is networking?
* Networking with TCP and HTTP
* Server/client building

## Quick Review of Asynchronous Return Values

## What is Networking?
* Connections?
* Communication between computers?
* Communication between multiple parties?

### Job Interview Networking
#### What should I be doing?
* Ask questions
* Be polite
* Give info about yourself
* Listen to the interviewer
* Greet the interviewer
* Wear a mask

#### What is the medium of communication?
* We use air to talk with sound waves
* We use ears to receive info

#### What about other communication media?
* Light
* Morse code
* Smoke
* Body language

Computers communicate in the same ways!

## Computer Communication
* Computer A (the client) connects to computer B (the server) via IP and PORT
  
  --- What is an IP?
    * The IP is the address: the exact location that the computer is at
    * Computers can have both a local IP and a global IP
    * Local IPs are only relevant in the local network!
    * Your router provides the GLOBAL IP
    * The router manages requests and assigns local IP addresses

  --- What is a PORT?
    * Imagine if a computer could only talk to one service at a time! Only connect to Zoom, or a website, or Slack, etc, and you have to leave one to use another
    * If a local IP is a building, then a PORT is like a floor number
    * Or if a local IP is a phone number, then a PORT is like an extension number!
    * A PORT, then, is a specific section where a program runs and is able to serve a server (or serve data) from!
    * ONE SERVER PER PORT!

  --- What is a SERVER?
    * A server is just a computer that is listening to a client!

1. The client connects.
2. The server listens.
3. The client asks for something.
4. The server evaluates the request and responds (either with the requested data or a refusal)
5. Repeat 2-4 until client disconnects.

## TCP
TCP stands for **Transmission Control Protocol**
  * It's just a set of rules for how computers talk to each other!
  * The previous steps are a loose definition of how TCP works!
  * There is a much more detailed definition available! Don't worry about it yet!

## HTTP
HTTP stands for **HyperText Transfer Protocol**
  * Every time you connect to a website, you're making an HTTP connection
  * HTTP is a *subset* of TCP: it uses the TCP connection but adds extra rules
    1. Client connects to server
    2. Client makes a request
    3. Server responds back
    4. Client connection terminates!
  * HTTP includes anutomatic termination of the connection, whereas TCP keeps the connection open until someone actually disconnects!

## Node's NET Package
The **`net`** package is built-in to node and helps abstract a lot of the complexity of connections!

* SOCKET: A single specific connection between one server and one client.