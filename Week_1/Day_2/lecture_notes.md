# Week 1 Day 2: The Dev Workflow

## Curriculum Overview

### Fundamental Fridays
* Learn more about fundamental CS topics on these days
* Programming tests: help practice for coding tests and review weekly concepts
* Research and Reflect (RnR): Write on a subject of your choosing

### Week 1
* Focus on FOCAL (functions, objects, conditionals, arrays, loops)
* Dev approach: code style/quality, testing, debugging, problem-solving
* FF: Mock programming test #1 and Recursion

### Week 2
* Asynchronous flow (callbacks/promises)
* FF is OOP

### Week 3
* Build an actual web app - HTTP Servers, express.js, cookies, basic html/forms
* FF: Data structures

### Week 4
* Front-end work, client-side JS/broswers, etc
* FF: ALgorithm complexity

### Week 5
* Data - databases, SQL, etc
* FF: Project/midterm kickoff
  * We have a week to make a project w/ teammates for midterm

### Week 6 Project
* Intro to project management, lifecycle, collab
* Project defined by LHL
* FF: demo to peers on friday, plus career/resume prep

### Weeks 7-10
* Modern web stacks/frameworks
* React, Ruby on Rails, libraries

### Weeks 11-12
* Final project, project is defined by me/team!
* No FF

### Solo Projects
* Four real-life-related projects
* Week 3: URL shortener
* Week 4: Twitter clone
* Weeks 7/8: Interview scheduler (calendar style)
* Weeks 9/10: Ecommerce app (like amazon)

### Programming tests
* 6 in total

### Tech interviews
* 3 total
* Weeks 2, 4, 9

## How to Approach Lectures
* Participate!
* Ask questions!
* Be engaged!
* Keep the camera on!

### Coding Examples
* Take notes and pay attention, but the goal is NOT to recreate the instructor's code
* The question is not "what did the instructor do" but "WHY did they do it in the way they did?"

### First coding example
#### Difference between function EXPRESSIONS (`const foo = function() {};`) and function DECLARATIONS (`function someFunction() {}`)
* Why do we do expressions and not declarations?
* Because a function declaration can OVERWRITE an existing function!
* That means we could accidentally re-define a function from earlier in the code, or from an imported library! BAD
* Whereas if we declare it with `const` then it can't be reassigned! We'll get us an error if we try, so we're alerted to the problem before it affects our program!
* EXCEPTION: In React.js, when we try to export functions ("components" in React), it takes extra code to use `const` rather than a declaration

#### What about arrow functions?
* More useful for callbacks than for other purposes, a declaration suffices for most other situations

### Second coding example
* sum.js - get inputs from terminal and sum them
* Start with what we have (input) and what we want (output)
* Then we can describe how we're going to do it
* `process` is an object with a lot of useful information, not just argv! It has all of the current Node information in it.
* A postmortem is important! Take note of what you forgot to do, or what went wrong, so you can remember it next time!'
* Even if you're doing an independent example (like sum.js), it's still a good idea to plan in pseudocode and put your code in functions!
* Big thing for today: START BY PLANNING! You're skipping too many steps, start with comments on EVERY EXERCISE.

## GitHub
* It's a bit easier to create a directory, then make a repo from that directory name, then init the repo from the command line and sync it up
* Start using "main" instead of "master"
* git push -u origin main will set it so that you can just say "git push" in the future and it will automatically push to that branch