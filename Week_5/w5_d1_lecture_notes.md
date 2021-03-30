# Databases

## What is a database?
It's a structure for storing data, but it's more than *just* that. It's a scalable solution for allowing LOTS of people to store and access LOTS of data quickly, accurately, and reliably.

The bare minimum is **persistence**: data doesn't disappear when the computer/server/app/whatever shuts down.

Beyond that is **permanence**: data doesn't go away. Period. Unless maybe you specifically try very hard to delete it?

## Okay, so...
Okay let's go back a step. A **database** is an organized collection of persistent data, saved for use at a later date. It's the third tier of web dev architecture: Client -- Application -- Data.

## Database Management Systems

## Types of Databases
- Relational
- Key-value
- Column-store
- Graph databases
- Document databases (JSON-like format)
- Real-time databases

Mostly we're talking about RELATIONAL databases.

## Relational Databases

These databases store data in tables, and relate those tables together with `keys`.

## SQL

SQL stands for Structured Query Language, and it's been around since the early 70s.

It's a **declarative** language, rather than an **imperative** language. What does that mean? I'm not positive! We'll figure it out later.

**`ALL SQL STATEMENTS SHOULD END WITH A SEMICOLON`**

## psql

`psql` is the command-line interface we'll be using to connect to PostgreSQL. It needs an instance of PostgreSQL *running* to work - similar to a browser trying to connect to a server, the server must be running!

### Making a database

`CREATE DATABASE jokes`

the end. that was easy.

- `\!` lets you run normal terminal commands from within psql
- `\i` lets you import sql files to run the commands within them

### Inserting data

```SQL
INSERT INTO
table (data1, data2, data3)
VALUES
(line1val1, line1val2, lineval3),
(line2val1, line2val2, line2val3),
(line3val1, line3val2, line3val3);
```

This will insert 3 separate rows of data all at once instead of needing separate statements for each!

### Seed Data

"Seed data" means the initial values in a database when it's created, and they're usually only on the dev side.

### JOINING Tables

You want to join on a specific ID!