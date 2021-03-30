# ERD, Datatypes, and Normalization

## ERD

### What is an ERD?

An ERD (Entity Relationship Diagram) is a diagram showing the structure of a database, and how the data within it relates to each other.

A well-made ERD helps organize a database before it exists, and helps make sure that all the data within is searchable, accessible, and organized in a scalable, sensible manner.

### Naming Conventions
- We must have **tables**
  - Each table must have a single type of **entity**
  - Each table may contain multiple **instances** of that entity 
  - Each instance must have a unique **primary key (PK)**
  - Table names may be singular or plural depending on preference
- We must have **columns**
  - Each column must have a single **type** of data
  - Each column name must be a singular noun (`email`, `password`, `user_id`)
  - Some data types are better than others for specific use cases, and it might not always be obvious!
    - For instance, to avoid rounding issues, prices are usually stored as `INTEGER` types, in cents rather than in dollars!

### Relationships

- Tables can be **related** to each other with **foreign keys (FK)**
- Tables can have one-to-one or one-to-many relationships
- Tables that require many-to-many relationships MUST use a **bridge table**
  - For instance: a class can have many students, a student can take many classes.
  - We need a bridge table called **rosters** or something (**students_classes** is acceptable too)
- These relationships are enforced by the language used when writing each table, using keywords like **UNIQUE** and **REFERENCES**

## Normalization

**Database normalization** is the process of taking data from non-relational sources and creating relationships.

Normalization has different levels! You generally go through it in stages.

Sometimes "ideal" normalization isn't *necessary* or desirable, because joining data is costly! Sometimes non-normalized data is *faster* to work with in terms of computing speed.